---
title: 'Role Based Security Basics'
metadata:
    description: 'Security Guide Role Based Security Basics'
    author: 'Joe Bordes'
content:
    items:
        - '@self.children'
    limit: 5
    order:
        by: date
        dir: desc
    pagination: true
    url_taxonomy_filters: true
taxonomy:
    category:
        - security
        - manual
        - securityguide
    tag:
        - guide
        - role
---

## Introduction

coreBOS implements a state of the art role-based security management
which utilizes the concepts of roles, similar to the implementation of
security in many current computer operating systems. Role-based security
(also called role-based access control) is built on the premise that
users are authenticated, which is the process of identifying the user.
Once identified, the user can be authorized or, assigned roles and permissions.

Note: Role-based security specifies and enforces enterprise-specific
security policies in a way that maps naturally to an organization's structure.

The basis is browsing, delete, create and update permissions given to
the individual users.

Role-based security has become the predominant model for advanced access
control because it reduces the complexity and cost of security administration.

Note: Although role-based security is the main security component at the
CRM system, the overall outcome of the security settings at the CRM
system is also influenced by the default organization settings.

While role-based security may be overkill in trivial settings (e.g.
small enterprises with two users who both are allowed to browse, delete
or update all data) it is an extremely powerful tool to get a handle on
complex environments. That includes typical company settings where
various sales teams or customer service teams need to browse, delete or
update customer related data while at the same time permissions on such
data may vary depending on the function or task of the employee within the company.

Although role-based security does not promote any protection policy, it
has been shown to support several well-known security principles and
policies that are important to commercial and government enterprises
that process unclassified but sensitive information. These policies can
be enforced at the time profiles are authorized for a role, at the time
users are authorized as members of a role, at the time of role
activation (e.g., when a role is established as part of a user's active
session), or when a user attempts to perform an operation on data.

## Role-based Security Features and Supporting Policies

This section explains the features provided by the security settings.
Policies are described in terms of users, roles, role hierarchies,
profiles, protected fields, and user groups.

Note: Setting up user privileges might not be a trivial task especially
in larger organizations. You will need a deep understanding of the
role-based security concept to give each individual user the access to
the CRM they desire.

The security management includes the configuration of the following CRM modules:

- Users
- Roles
- Profiles
- Groups
- Default Organization Sharing Access
- User Defined Sharing Rules
- Default Organization Field Access

Important: Security settings will become valid not until the next user Login!

The following sections will explain how these CRM modules can be used.

### Users

here are two types of users for the CRM software:  

- Standard user
- Administrator user

Standard users have limited access to the CRM system to perform CRUD (Create, Retrieve, Update, and Delete) operations only.

Administrator users are capable to manage the complete software that includes:

- managing users/groups and their access privileges
- customizing the CRM user interface
- creating communications templates
- configuring all organization-wide settings
- change passwords, deactivate users, list mail server, change the home page order and view the login history
- exercise CRUD operations  

At `Figure: Special Admin Function` you see the edit view of a users data provided by the CRM user management function. With marking the Admin check box any user might get administration privileges and become an administrator user.

Figure 1.1. Special Admin Function

![Special Admin Function](adminfunction.png)

 !!! Administrator users have all privileges in the organization.

### Roles

At the core of role-based security is the concept of collecting
permissions in roles, which can be granted to standard users. Each role
is assigned one or more privileges (e.g., data access, deletion,
modification). It is a user's membership into roles that determine the
privileges the user is permitted to perform. Security administration
with role-based security consists of determining the operations that
must be executed by persons in particular jobs and assigning employees
to the proper roles. The role-based security framework provides for
mutually exclusive roles as well as roles having overlapping
responsibilities and privileges. For example, some general CRM
operations may be allowed by all employees, while other operations may
be specific to a role. Role hierarchies are a natural way of organizing
roles within an organization and defining the relationship and
attributes of the roles. Complexities introduced by mutually exclusive
roles or role hierarchies as well as regulating who can perform what
actions, are all handled by the role-based security settings.

One of role-based security greatest advantages is the administrative
capabilities it supports. User membership into roles can be assigned and
revoked easily and new memberships established as job assignments
dictate. With role-based security, users are not granted permission to
perform operations on an individual basis, rather, operations are
associated with roles. Role association with new operations can be
established as well as old operations deleted as organizational
functions change and evolve. This basic concept has the advantage of
simplifying the understanding and management of privileges. Roles can be
updated without having to directly update the privileges for every user
on an individual basis.

 !!! Each user created in the CRM system must be associated with a role. A role must be associated with at least one profile.

Individual users (e.g. John, Mary) might be assigned to one or more
roles, where the roles are based on the user's job responsibilities and
competencies in the organization. Users should be assigned multiple
roles to reflect the fact that some users connect to the system in
different function depending on the tasks. For example, user "John"
might be assigned the role "Head-Sales", because John is the head of
sales at your company, as well as the role "admin" because John is also
CRM system administrator. If John wants to work as an administrator he
logs in as "admin", if John wants to work as head of sales he logs in as
"Head-Sales". It is possible to let John connect to the system with the
same password, regardless of whether he acts as administrator or head of
sales.

 !!! Users at any given role can always view, edit, delete all data owned by users below in the hierarchy.

For the CRM system to reach its full potential as a means for enterprise
CRM, access control mechanisms must be in place that can regulate user
access to information in a manner that faces your business today.
Role-based security allows for the specification and enforcement of a
variety of protection policies which can be tailored on an
enterprise-by-enterprise basis. The purpose of the role-based security
setting is to provide this access control service. Once the role-based
security framework is established for the organization, the principal
administrative actions are the granting and revoking of users into and
out of roles as job assignments dictate. These maintenance tasks are
easily performed using the CRM system's user settings tool.

### Profiles

Profiles are used to define privileges for executing CRM system
operations. From a functional perspective, role-based securities central
notion is that of profiles representing actions associated with roles
and users that are appropriately made members of roles.

The relationships between users, roles, and profiles are depicted in `Figure: User, Role and Profile Relations` as a many-to-many relationship. For example, a single standard user can be
associated with one or more roles by different user names, and a single
role can have one or more user members. Roles can be created for various
job positions in an organization. For example, a role can include sales
representative or assistant in a company. The profiles that are
associated with roles constrain members of the role to a specified set
of actions. For example, within a sales organization the role of the
sales representative can include operations to create, edit, and delete
the own accounts; the role of an assistant can be limited to browse
existing information of a particular sales rep; and the role of the head
of sales may be to review all sales data.

**Figure 1.2. User, Role and Profile Relations**

![Figure: User, Role and Profile Relations](urp-relation.png)

The association of profiles with roles within an enterprise can be in
compliance with rules that are self-imposed. Profiles can be specified
in a manner that can be used in the demonstration and enforcement of
regulations. For example, an assistant can be constrained to adding a
new entry to a customers history rather than being generally able to
modify sales records.

Your access privileges to the CRM system are set by the administrator.
The administrator should set these privileges when configuring the CRM
system. Thereby the following privilege types are available:

- The permission to use certain CRM modules.
- The permission to view data in certain CRM modules.
- The permission to edit or to change data in certain CRM modules.
- The permission to delete data in certain CRM modules.
- The permission to export data from certain CRM modules.
- The permission to import data to certain CRM modules.

The CRM system makes sure that you can only exercise certain operations if you have proper privileges.

**Important**

Note the following rules:

- special privileges are always superior to common privileges
- revoked privileges overstrike always granted privileges
- at the CRM system there are special rules, please note the special rules marked as "Important"

Thereby, the CRM system distinguishes the following privilege types:

Global Privileges:

When you create a profile the global privileges allows you to decide whether the common privilege to view or to edit all information/modules of the coreBOS system is given:

- *View all*: user can view all module data in the organization
- *Edit all*: user can create/edit all module data in the organization

**Important**

Global Privileges in Profiles override the permissions defined by Tab,
Standard, Field, and Utility Privileges as they are explained below.  
For example, let us assume in a profile the access to the Potentials tab
is denied via Tab Privileges. Even then a standard user can view the
Potentials module data if the 'View all' permission is set in the Global
Privileges of the user's profile.

Tab Privileges:

The option to set tab privileges allow you to decide which tabs or
modules to be shown.

This includes the Leads, Accounts, Contacts, Potentials, Dashboards,
Activities, Trouble Tickets, FAQ, Calendar, Price Books, Purchase
Orders, Invoices, Reports, Notes, Emails, Products, Vendors, Quotes,
Sales Orders, RSS, and Campaigns modules.

Standard Privileges:

The option to set standard privileges allow you to decide whether to
Create or Edit, Delete, and View privileges are given related to the CRM
modules.

That includes the Leads, Accounts, Contacts, Potentials, Activities,
Trouble Tickets, FAQ, Price Books, Purchase Order, Invoices, Notes,
Emails, Products, Vendors, Quotes, and Sales Orders modules.

Field Privileges:

The option to set field privileges allows you to decide what entry field
for each CRM module will be available for roles that are based on this
profile.

That includes the Leads, Accounts, Contacts, Potentials, Activities,
Trouble Tickets, FAQ, Price Books, Purchase Orders, Invoices, Notes,
Emails, Products, Vendors, Quotes, and Sales Orders modules.

**Important**

Custom fields are included. Therefore, you should have created your custom fields first before you set the privileges.

Utilities:

Numerous CRM modules come with utility functions such as Import, Export,
Merge, and Convert Lead. The option to set utility privileges allows you
to decide whether these functions will be available for roles that are
based on this profile.

**Important**

Privileges defined by profiles override the Default Organization Sharing Rules and the User-defined Sharing Rules.

For example, let us assume that the organization sharing rule allows a user to view the Potentials of other users. However, if the profile does not allow to access the Potential module these access privileges are revoked.

### User Groups

Each data entry at the CRM system has an owner. Such an owner could be
an individual user or a group of users, called team. For better
manageability, several users, roles, roles with subordinates and user
groups can be collected in user groups. You may use this to assign data
entries to team

**Note** It is important to understand, that groups are not a tool for defining security settings. Rather user groups are used to manage the data access.

The following sections explain what a group membership means and how it can be used.

### Group of users

Users can be collected in groups. Let us assume we would like to build a
small group of sales representatives, called Team A as shown in `Figure: Group of Users Example.`

**Figure 1.3. Group of Users Example**

![Figure: Group of Users Example](sampleusergroup1.png)

Person 1 and Person 2 suppose to be the members of this group, so we
build a group of users. Each of these Persons is assigned to a role that
defines the security settings for the individual user. You may now
assign data sets to this group, as shown as an example in `Figure: Activity assigned to Group`. The assignment to this group means, that all members of this group are the owner of this entry.

**Figure 1.4. Activity assigned to Group**

![Figure: Activity assigned to Group](groupmeetingsample.png)

Therefore all CRM functions usually available for an owner for this entry are now available to all members of this group. That includes in this case:

- Permission to browse, modify or to delete this entry
- Listing of this activity at the calendar of each Person who is a member of this group

 ! Note that the group settings override the profile settings.

### Group of roles

You can also build groups that are based on roles. That might be a
helpful function if you do not know the individual users and their task
within your company. An example is shown in `Figure: Group of Roles Example`

**Figure 1.5. Group of Roles Example**

![Figure: Group of Roles Example](sampleusergroup3.png)

At this group, all users that have the role "Sales" or "Marketing" are
members of this group. If you assign a data entry at the CRM system to
this group, all members become the owner of this entry. In `Figure: Lead assigned to Group you see an example for a lead entry.

**Figure 1.6. Lead assigned to Group**

![Figure: Lead assigned to Group](groupleadsample.png)

All group members have now the permission:

- to browse, modify or to delete this entry
- to convert this lead to a sales potential
- to send a mail to the person listed

 ! Note that the group settings override the profile settings. Group privileges may get limited by custom organization sharing privileges.

### Group of roles with subordinates

In addition to simple role based groups you may also build groups that
include subordinates. That means the users who are assigned to roles
which are below a selected role will be included. The following figures
illustrate that. Let's assume your company has set up a hierarchical
order as shown in `Figure: Hierarchy Example`

**Figure 1.7. Hierarchy Example**

![Figure: Hierarchy Example](hierarchiesample.png)

In this figure, the role "Sales" has a subordinated role "Sales
Assistant" and the role "Marketing" is the master of the role "Marketing
Assistant". If you create a user group as shown in `Figure: Group of Roles with Subordinates` all users with sales and marketing related roles, including the assistants will become members of this group.

**Figure 1.8. Group of Roles with Subordinates Example**

![Figure: Group of Roles with Subordinates](sampleusergroup4.png)

If you assign a CRM data entry to this group all users who are a member
of this group will become the owner. Related to the example shown in `Figure: Potential assigned to Group` that means:

- All members of this group are allowed to browse, modify or to delete this entry

**Figure 1.9. Potential assigned to Group**

![Figure: Potential assigned to Group](grouppotentialsample.png)

 ! Note that the group settings override the profile settings. Group privileges may get limited by custom organization sharing privileges.

### Group of Groups

You may build groups where the members are also groups. That means, that
all users who are a member of a selected group will also become members
of the new group. Let's assume you would like to build a hierarchy as
shown in `Figure: Sample Hierarchy for Groups`. Based on this structure
you may create a user group "Sales" where the groups "Team A" and "Team
B" are members. At this example, the "Team A" and Team B" groups are
built with users as members.

**Figure 1.10. Sample Hierarchy for Groups**

![Figure: Sample Hierarchy for Groups](sampleusergroup2.png)

If you assign a CRM data entry to the group "Sales" the Persons 1-4 will
become the owner of this entry with all rights related to owners.

 ! Note that the group settings override the profile settings. Group privileges may get limited by custom organization sharing privileges.

### Organisation Wide Sharing Privileges

The CRM system allows you to set default privileges that are valid
organization-wide. It is the purpose of these privileges to give an
administrator tool that allows a fast overall security setting.

### Default Organization Sharing Privileges

Default Organization Sharing Access controls data sharing at the
organization level. Global, as well as Custom Access Privileges, are
offered.

 !!! Profiles always override the organization-wide sharing privileges!

### Global Access Privileges

The CRM system comes with default global organization sharing privileges for the most important CRM modules as shown in `Figure: Default Global Privilege Settings for Organization`. Default Organization Sharing Access controls data sharing at the organization level.

**Figure 1.11. Default Global Privilege Settings for Organization**

![Figure: Default Global Privilege Settings for Organization](ospriviledges.png)

The following sharing permission types can be set:

**Table 1.1. Sharing Permission Types**

<table class="table table-striped">
<thead>
<tr class="header">
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Private</td>
<td>Only the record owner, and users with a role that is above of the record owners role in the hierarchy can browse, edit, delete and report on those records.</td>
</tr>
<tr>
<td>Public Read Only</td>
<td>All users can view and report on records but not edit them. Only the owner and users with a role that is above of the record owners role in the hierarchy can edit or delete those records.</td>
</tr>
<tr>
<td>Public Read/Write</td>
<td>All users can view, edit all records. Only the owner and users with a role that is above of the record owners role in the hierarchy can delete those records.</td>
</tr>
<tr>
<td>Public Read/Write/Delete</td>
<td>All users can view, edit and delete all records.</td>
</tr>
</tbody>
</table>

**Important** Please note the following rules:

- Default organization sharing privileges are overridden by profile settings.
- For Activities module the default organization sharing privilege value is set to the fixed value Private and cannot be altered.
- Regardless of the organization-wide defaults, users can always view and edit all data owned by or shared with users below them in the role hierarchy if not prohibited by the profile.
- When an Account has been set to Private, the access to related potentials, tickets, quotes, sales orders, purchase orders, and invoices is also set to private. You must have at least read access to a record to be able to add activities or other associated records to it.

### Custom Access Privileges

User-defined sharing rules set by Custom Access Privileges allows the
administrators to selectively grant data access to a set of users. Data
sharing rules can be created to share data between the following modules:

- From Role to Role
- From Role to Role Subordinates
- From Role to Group
- From Role Subordinates to Role
- From Role Subordinates to Role Subordinates
- From Role Subordinates to Groups
- From Group to Role
- From Group to Role Subordinates
- From Group to Group  

Sharing Rules can be created for the following modules:

**Leads Sharing Rules:**

Leads owned by the users of a given Role/Role Subordinates/Group can be
shared with users of another Role/Role Subordinates/Group with Read Only
or Read/Write permission. Emails related to a lead will also be shared
with Read Only or Read/Write permission.

**Accounts Sharing Rules:**

Accounts owned by the users of a given Role/Role Subordinates/Group can
be shared with users of a Role/Role Subordinates/Group with Read Only or
Read/Write permission.

Emails related to a lead will also be shared with Read Only or Read/Write permission.

 !!! Sharing Rules created for Accounts module will also apply to the contacts module automatically.

**Potentials Sharing Rules:**

Potentials owned by the users of a given Role/Role Subordinates/Group
can be shared with users of a Role/Role Subordinates/Group with Read
Only or Read/Write permission.

Quotes and Sales Order related to a potential will also be shared with
Read Only or Read/Write permission.

**HelpDesk Sharing Rules:**

Tickets owned by the users of a given Role/Role Subordinates/Group can
be shared with users of a Role/Role Subordinates/Group with Read Only or
Read/Write permission.

**Email Sharing Rules:**

Emails owned by the users of a given Role/Role Subordinates/Group can be
shared with users of a Role/Role Subordinates/Group with Read Only or
Read/Write permission.

**Quotes Sharing Rules:**

Quotes owned by the users of a given Role/Role Subordinates/Group can be
shared with users of a Role/Role Subordinates/Group with Read Only or Read/Write permission.

Sales Orders related to a quote will also be shared with Read Only or Read/Write permission.

**Purchase Order Sharing Rules:**

Purchase Orders owned by the users of a given Role/Role
Subordinates/Group can be shared with users of a Role/Role
Subordinates/Group with Read Only or Read/Write permission.

**Sales Order Sharing Rules:**

Sales Order owned by the users of a given Role/Role Subordinates/Group
can be shared with users of a Role/Role Subordinates/Group with Read
Only or Read/Write permission.

Invoices related to a sales order will also be shared with Read Only or
Read/Write permission.

**Invoice Sharing Rules:**

Invoices owned by the users of a given Role/Role Subordinates/Group can
be shared with users of a Role/Role Subordinates/Group with Read Only or
Read/Write permission.

**Important** Please note the following rules:

- Custom Sharing Rules can only extend the visibility and cannot hide visibility.
- Sharing Rules cannot be specified to share data between two users. (for a solution see Section: Example 1)
- Sharing rules apply to all existing data and the data which will be added in future.
- The number of sharing rules which can be defined for a single Role, Role Subordinates or Group is not limited.

### Default Organization Fields Access

Default Organization Field Access function is used to control the
visibility of fields in various modules for the entire organization. You
can use this function to define your organization-wide filed access and
to either show or hide a field to the entire organization.

By default, the CRM is configured that all master data provided with the CRM system are shown and can be edited. As an example in `Figure: Fields Manager Activities` you see the default fields for activities. If you want to restrict access to specific fields you can edit and change the settings for each individual CRM module.

**Figure 1.12. Fields Manager Activities**

![Figure: Fields Manager Activities](ofpriviledges.png)

 !!! Default field access settings include custom fields you may have created before.

Default Organization Field Privileges can be defined for the following
modules: Leads, Accounts, Contacts, Potentials, Activities, Trouble
Tickets, FAQ, Price Books, Purchase Order, Invoice, Notes, Emails,
Products, Vendors, Quotes, and Sales Orders.

**Important**

- It is not possible to disable the mandatory fields in the modules.
- Default Organization field access overrides the profile level field access.

For example, let us assume a profile allows to view the website field in leads. However, if this field has not been enabled at the organization level field access settings it will not be shown.

------------------------------------------------------------------------

[Next](../03.Examples) | Chapter 2. Examples

------------------------------------------------------------------------

© 2006 crm-now
