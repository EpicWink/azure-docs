---
title: Configure PIM for Groups settings (preview) - Azure Active Directory
description: Learn how to configure PIM for Groups settings (preview).
services: active-directory
documentationcenter: ''
author: amsliu
manager: amycolannino
ms.service: active-directory
ms.topic: how-to
ms.tgt_pltfrm: na
ms.workload: identity
ms.subservice: pim
ms.date: 01/12/2023
ms.author: amsliu
ms.custom: pim
ms.collection: M365-identity-device-management
---

# Configure PIM for Groups settings (preview)

In Privileged Identity Management (PIM) for groups in Azure Active Directory (Azure AD), part of Microsoft Entra, role settings define membership/ownership assignment properties: MFA and approval requirements for activation, assignment maximum duration, notification settings, etc. Use the following steps to configure role settings – i.e., setup the approval workflow to specify who can approve or deny requests to elevate privilege.

You need to have Global Administrator, Privileged Role Administrator, or group Owner permissions to manage settings for membership/ownership assignments of the group. Role settings are defined per role per group: all assignments for the same role (member/owner) for the same group follow same role settings. Role settings of one group are independent from role settings of another group. Role settings for one role (member) are independent from role settings for another role (owner).


## Update role settings

Follow these steps to open the settings for a group role. 

1. [Sign in to Azure AD portal](https://aad.portal.azure.com).

1. Select **Azure AD Privileged Identity Management -> Groups (Preview)**. 

1. Select the group that you want to configure role settings for.

1. Select **Settings**.

1. Select the role you need to configure role settings for – **Member** or **Owner**.

   :::image type="content" source="media/pim-for-groups/pim-group-17.png" alt-text="Screenshot of where to select the role you need to configure role settings for." lightbox="media/pim-for-groups/pim-group-17.png":::

1. Review current role settings.

1. Select **Edit** to update role settings. 

    :::image type="content" source="media/pim-for-groups/pim-group-18.png" alt-text="Screenshot of where to select Edit to update role settings." lightbox="media/pim-for-groups/pim-group-18.png":::

1. Once finished, select **Update**.

## Role settings

### Activation maximum duration

Use the **Activation maximum duration** slider to set the maximum time, in hours, that an activation request for a role assignment remains active before it expires. This value can be from one to 24 hours.

### Require multi-factor authentication (MFA) on activation

You can require users who are eligible for a role to prove who they are using Azure AD Multi-Factor Authentication before they can activate. Multi-factor authentication ensures that the user is who they say they are with reasonable certainty. Enforcing this option protects critical resources in situations when the user account might have been compromised.

User may not be prompted for multi-factor authentication if they authenticated with strong credential or provided multi-factor authentication earlier in this session.

For more information, see [Multifactor authentication and Privileged Identity Management](pim-how-to-require-mfa.md).

### Require justification on activation

You can require that users enter a business justification when they activate the eligible assignment.

### Require ticket information on activation

You can require that users enter a support ticket when they activate the eligible assignment. This is information only field and correlation with information in any ticketing system is not enforced.

### Require approval to activate

You can require approval for activation of eligible assignment. Approver doesn’t have to be group member or owner. When using this option, you have to select at least one approver (we recommend to select at least two approvers), there are no default approvers.

To learn more about approvals, see [Approve activation requests for privileged access group members and owners (preview)](groups-approval-workflow.md).

### Assignment duration

You can choose from two assignment duration options for each assignment type (eligible and active) when you configure settings for a role. These options become the default maximum duration when a user is assigned to the role in Privileged Identity Management.

You can choose one of these **eligible** assignment duration options:

| | Description |
| --- | --- |
| **Allow permanent eligible assignment** | Resource administrators can assign permanent eligible assignment. |
| **Expire eligible assignment after** | Resource administrators can require that all eligible assignments have a specified start and end date. |

And, you can choose one of these **active** assignment duration options:

| | Description |
| --- | --- |
| **Allow permanent active assignment** | Resource administrators can assign permanent active assignment. |
| **Expire active assignment after** | Resource administrators can require that all active assignments have a specified start and end date. |

> [!NOTE]
> All assignments that have a specified end date can be renewed by resource administrators. Also, users can initiate self-service requests to [extend or renew role assignments](pim-resource-roles-renew-extend.md).

### Require multi-factor authentication on active assignment

You can require that administrator or group owner provides multi-factor authentication when they create an active (as opposed to eligible) assignment. Privileged Identity Management can't enforce multi-factor authentication when the user uses their role assignment because they are already active in the role from the time that it is assigned.
User may not be prompted for multi-factor authentication if they authenticated with strong credential or provided multi-factor authentication earlier in this session.

### Require justification on active assignment

You can require that users enter a business justification when they create an active (as opposed to eligible) assignment.

In the **Notifications** tab on the role settings page, Privileged Identity Management enables granular control over who receives notifications and which notifications they receive.

- **Turning off an email**<br>You can turn off specific emails by clearing the default recipient check box and deleting any other recipients.  
- **Limit emails to specified email addresses**<br>You can turn off emails sent to default recipients by clearing the default recipient check box. You can then add other email addresses as recipients. If you want to add more than one email address, separate them using a semicolon (;).
- **Send emails to both default recipients and more recipients**<br>You can send emails to both default recipient and another recipient by selecting the default recipient checkbox and adding email addresses for other recipients.
- **Critical emails only**<br>For each type of email, you can select the check box to receive critical emails only. What this means is that Privileged Identity Management will continue to send emails to the specified recipients only when the email requires an immediate action. For example, emails asking users to extend their role assignment will not be triggered while an email requiring admins to approve an extension request will be triggered.

## Next steps

- [Assign eligibility for a group (preview) in Privileged Identity Management](groups-assign-member-owner.md)
