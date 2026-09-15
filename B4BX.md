# BrokerX New Business Requirements

*Source: [https://bizcover.atlassian.net/wiki/spaces/BFB/pages/4800020488/BrokerX+New+Business+Requirements](https://bizcover.atlassian.net/wiki/spaces/BFB/pages/4800020488/BrokerX+New+Business+Requirements)  
Author: Mireille Levitan  
Last modified: yesterday at 11:07 AM*

---

**BrokerX New Business Requirements**

Functional Requirements — New Broker Portal, New Business

**Note:** *This document draws on BizCover's Business Analysis Toolkit (product documentation and source-code repositories), Confluence and Jira. Please review carefully.*

**Stakeholders**

| **Name** | **Role** | **Date Approval** | **Approval** |
| --- | --- | --- | --- |
| Peta Furlong | Senior Operations & Distribution Manager -Broker |   |   |
| Kimberley O’Donnell | Broker Team Coordinator |   |   |
| Catherine Thompson | Broker Team Coordinator |   |   |
| Dante Phan | Team Lead - AI and Integration - Technology |   |   |
| Elena Li | AI Engineer Technology |   |   |
| Adriana Rey | Growth Marketing Specialist -Broker |   |   |
| Bradley Hoyle | Manager Operational Excellence - Operations |   |   |



**Version Control**

| **Date** | **Name** | **Comment** |
| --- | --- | --- |
| 04/09/2026 | Mireille Levitan | Draft |
| 08/09/2026 | Mireille Levitan | Additon to Brokers Screen Addition to Quote Compare Addition to Summary Window for promotion Code |

  


# Overview

## Purpose

The project rebuilds BizCover 4 Brokers (B4B) on the BlazeX back end, replacing its current MVC-based platform and direct-derived front end with a purpose-built broker quoting experience. It serves a dual strategic purpose: advancing BizCover's broader MVC-to-BlazeX re-platforming effort while giving brokers a best-in-class quoting front end designed around their workflows to support growth of the broker channel. The rebuild is intended to be cost-disciplined, reusing existing functionality from Blaze-X, Agent-X and Aurora rather than building extensive new back-end capability.

The New Business portion of the new Broker Portal enables brokers to create, price, approve, and convert customer quotations into bound policies while enforcing pricing and approval policies.

## Scope

### In Scope

- Log On to System
- Menu
- Create quotes
- Edit quotes
- Referrals
- Apply discounts
- Approval workflows
- Generate PDF quotes
- Convert quotes to bound policies
- AI Assistance

### Out of Scope

- Full MVC decommissioning, since that also depends on AUB brokers migrating separately via Aurora.
- Contract management
- Billing
- Invoice generation
- Initial phase is only for the Australia (AU) region

## Business Objectives

- Reduce quote creation time
- Improve pricing accuracy
- Standardize approval processes
- Increase quote-to-order conversion rates
- Use of AI to assist the broker in making more accurate and efficient sales.
- Grow the broker channel.

## Actors

| **Role** | **Responsibility** |
| --- | --- |
| Brokers | Creates quotes |
| Administrator | Assist with getting quote issues resolved and policies bound. |

## Process Overview of New Business Process

## Below is a brief summary of the process flow. The detailed flow can be found at the link:  <u>https://bizcover.atlassian.net/wiki/spaces/BFB/pages/4761157639/Broker+X+-+Design+New+Business+1?atlOrigin=eyJpIjoiMmI4MDIxMjBlMDBjNGI0ZDljMTgxNDg4OTU5NDJhYzMiLCJwIjoiYyJ9</u>

*[embedded media/image omitted]*















**A10: Customer Details**

Broker/Administrator searches and selects the customer's business occupation. System retrieves LMI and ANZSIC codes. The user cannot proceed without valid occupation selection. The user also enters some basic information such as Insured Name, Policy Inception Date, Policy Expiry date and Address. 

**B10: Product Selection**

Broker/Administrator selects insurance products, and answers preliminary underwriting questions. System creates Journey and displays Journey ID.

**C10: Business Details **

 Broker/Administrator enters activity split and occupation as specified per Insurer. System auto-saves progress.

**D10: Underwriting**

Broker/Administrator answers questions specific to the products being chosen and the client’s particular circumstances.

**E10: Interested Parties**

The name, address and reason for interest are added for any additional interested parties.

**F10: General Questions**

Questions related to the locations of business, claims behaviour, and stamp duty are presented to the user. On completing this section, the quotation can occur.

**G10: Quote **

System generates quotes from multiple insurers. Broker/Administrator can compare policies, edit quote (premium adjustment), manage endorsements, and email quote to customer. At this point the user may also refer to the insurer if additional underwriting is required.

**H10: Bind Policy**

Broker/Administrator enters legal entity details, acknowledges terms, and submits. 

**I10: Payment and Summary**

On business sold by Brokers no payment is actioned at New Business however the payment amount and frequency are shown. A summary of policy details is also shown.

**J10: Policy Bound Successfully**

System binds policy and displays policy number and informs broker /administrator that the policy has been emailed to the broker.



  


# Functional Requirements

## Login

### Data Requirements

| **Field** | **Mandatory** | **Format** |
| --- | --- | --- |
| Email Address | Yes | Text |
| Password | Yes | Text |
| Login |   | Button |
| Forgot Password |   | Button |
| Send Reset link |   | Button |
| Back |   | Button |
| New password | Yes | Text |
| Re-enter new password | Yes | Text |
| Reset password |   | Button |
| Logout |   | Button |
| Yes log out |   | Button |
| Stay logged in |   | Button |





### Business Requirements

**Log-01 —Email and password access.**

**Detail**

- Login must authenticate the broker via email/password (unlike the customer portal’s password less magic link).

 

**Acceptance Criteria**

**Given**** **a broker or administrator wants to access the BrokerX platform

**When**** **he lands on the system ask for a login and password.

**Then**** **he enters an email and password on the Broker Login page & he submits the form.

*Scenario 2:*

**Given **a broker or administrator has selected the login button

**When **a broker or administrator has entered an incorrect password

**Then **display** **the message** "Invalid user or password combination”.**

**Log-02 —2FA gates all broker access.**

**Detail**

- Hand off to two-factor authentication before granting access to the menu screen.

 

**Acceptance Criteria**

**Given **2 factor authentication is a security requirement.

**When **the broker or administrator login and his user and password are valid

**Then **redirect him to a second authentication factor before rendering any broker menu. If this step is not complete, deny access.

**Log-03 — Forgot Password**

**Detail**

On the login page there must be a “Forgot Password” button which routes the user to a page where he can enter his email and email will be sent to him to carry out a process to “Recover his password”

**Acceptance Criteria**

**Given **that a broker has forgotten his password

**When **he selects the “Forgot password” button 

**Then** he should be routed to a page to enter his email address to trigger the recover password process.

*Scenario 2:*

**Given **a broker or administrator has selected the login button

**When **a broker or administrator has entered an incorrect password

**Then **display** **the message** "Invalid user or password combination”.**



**Log-04 — Reset Password**

**Detail**

When a broker or administrator selects the Forgot Password link, send an email. When the user clicks the link in the email, direct the user to the Reset Password page, where they must enter and confirm a new password.

 

Upon selecting the Reset Password button:

·       If the New Password and Confirm Password fields match, redirected the user to the login screen and display the following message:

"Your password was successfully reset. You may now log in using your new password."

·       If the New Password and Confirm Password fields do not match, the user remains on the Reset Password page, and display the following error message:

"Passwords do not match."

**Acceptance Criteria**

**Given **a user has selected the Reset Password link

**When **he receives an email on forgetting his password

**Then **direct him to the Reset Password page.

*Scenario 2*:

**Given **that user has entered the fields New Password and Renter Password

**When **the fields match

**Then **redirect the user to the login screen and display the following message:

"Your password was successfully reset. You may now log in using your new password."

*Scenario 3:*

**Given** that user has entered the fields New Password and Renter Password

**When **the fields do not match,

**Then** the user remains on the Reset Password page, and display the following error message:

"Passwords do not match."

**Log-05 — "What's New" content**

**Detail**

Broker team leadership must be able to update the "What's New" panel content on a regular basis via an admin tool, without requiring a UI code release.

When a broker has authenticated – the what’s new page must display links to article’s, forms or other documentation which is new.

**Acceptance Criteria**

**Given **a broker-leadership user with content-admin access

**When **they update the "What's New" copy or links in the backend tool

**Then **the change is reflected on the next page load without a deployment.

*Scenario 2*:

**Given **that Bizcover wants to share information with brokers

**When **the broker has logged in successfully

**Then **the What’s New page should be displayed, and the broker should be able to select items by clicking on the relevant link.

  


## Menu

### Data Requirements

| **Tab** | **Field** | **Mandatory** | **Format** |
| --- | --- | --- | --- |
|   | Person Icon | Select | Button |
|   | Quotes | Select one | Button |
|   | Clients | Select one | Button |
|   | Referrals | Select one | Button |
|   | Renewals | Select one | Button |
|   | Search | Select one | Button |
|   | Resources | Select one | Button |
| Person Icon | **Account Details** |
| Person Icon | First Name | Yes | Text |
| Person Icon | Last Name | Yes | Text |
| Person Icon | Email Address | Prefilled & locked | Text |
| Person Icon | Business Address | Yes | Text |
| Person Icon | Post Code | Yes | Numeric |
| Person Icon | Phone | One is Mandatory Yes | Numeric |
| Person Icon | Mobile | One is Mandatory Yes | Numeric |
| Person Icon | Close | Yes | Button |
| ~~Person Icon~~ | ~~Apply Changes~~ | ~~Yes~~ | ~~Button~~ |
| Person Icon | **Change Password** |
| Person Icon | Current Password | Yes | Text |
| Person Icon | New Password | Yes | Text |
| Person Icon | Confirmed New Password | Yes | Text |
| Person Icon | Apply Changes | Yes | Button |
|   |
| Quotes | Describe Your Business | No | Button |
| Quotes | Web Search | No | Button |
| Quotes | Upload | No | Button |
| Quotes | Search | No | Search Box |
| Quotes | **Customer Quotes** |
| Quotes | Transaction Ref/Journey Code |   | Text Output |
| Quotes | Legal Entity Insured Name |   | Text Output |
| Quotes | Date Created |   | Date -format DD/MM/CCYY |
| Quotes | Expiry Date |   | Date -format DD/MM/CCYY |
| Quotes | Email Quote | No | Button |
| Quotes | Duplicate Quote | No | Button |
|   |
| Referrals | Search | One must be selected | Drop Down |
| Referrals | Search Button | Yes | Button |
| Referrals | Name of Insured |   | Output |
| Referrals | Transaction Ref |   | Output |
| Referrals | Policy Number |   | Output |
| Referrals | Policy |   | Output |
| Referrals | Created |   | Output – Date format DD Month YYYY |
| Referrals | Action | No | Button – surfacing Drop Down List |
| **Note:** 2 tables with same fields – 1 for Open Referrals and one for Closed/Expired referrals |
| Referral Details | Duplicate Application |   | Button |
| Referral Details | **Business Profile** |
| Referral Details | Legal Representative -First Name |   | Output |
| Referral Details | Legal Representative - Position |   | Output |
| Referral Details | Legal Entities -Legal Name *(can be multiple occurrence) * |   | Output |
| Referral Details | Legal Entities Business Name *(can be multiple occurrence)* |   | Output |
| Referral Details | Legal Entities -ABN *(can be multiple occurrence)* |   | Output |
| Referral Details | Legal Entities-Trading Name *(can be multiple occurrence)* |   | Output |
| Referral Details | **Preliminary Questions *****(Multiple Occurrences)*** |
| Referral Details | Preliminary Question |   | Output |
| Referral Details | Preliminary Answer |   | Output |
| Referral Details | **Underwriting Questions *****(Multiple Occurrences per Product)***** ** |
| Referral Details | Underwriting Question |   | Text |
| Referral Details | Underwriting Answer |   | Output |
| Referral Details | Activity (multiple occurrences) |   | Output |
| Referral Details | Resume |   | Button |
| Referral Details | Close |   | Button |
|   |
| Clients | Selection | One must be selected to proceed | Drop Down |
| Clients | Search Button | Yes | Button |
| Clients | Name of Insured |   | Output |
| Clients | Transaction Ref |   | Output |
| Clients | Policy Number |   | Output |
| Clients | Policy |   | Output |
| Clients | Effective |   | Output – Date format DD Month YYYY |
| Clients | Expiry |   | Output – Date format DD Month YYYY Button |
| Clients | Action | No | Button – surfacing Drop Down List |
|   |
| Renewals | Name of Insured |   | Output |
| Renewals | Transaction Ref |   | Output |
| Renewals | Policy Number |   | Output |
| Renewals | Policy |   | Output |
| Renewals | Status |   | Output |
| Renewals | Inception |   | Output – Date format DD Month YYYY |
| Renewals | Effective |   | Output – Date format DD Month YYYY |
| Renewals | Expiry |   | Output – Date format DD Month YYYY Button |
| Renewals | Action |   | Button – surfacing Drop Down List |
|   |
| Search | Enter Search text | Yes | Text |
| Search | Search Button | Yes | Button |
| Search | Copy of Journey Details | Optional | Button |
| Search | Transaction Ref/Journey Code |   | Output |
| Search | Inception Date |   | Output |
| Search | Expiry Date |   | Output |
| Search | Status |   | Output |
| Search | Occupation |   | Output |
| Search | Created |   | Output |
| Search | Last Updated By |   | Output |
| Search | Last Updated Date |   | Output |
| Search | Number of Policies in Journey |   | Output |
| Search | **Latest policy Details** |
| Search | Select | Optional | Tick Box |
| Search | Policy Number |   | Output |
| Search | Product Type |   | Output |
| Search | Insurer |   | Output |
| Search | Premium |   | Output |
| Search | Expiry Date |   | Output |
| Search | Actions | Optional | Button |
| Search | Number of Rows Selected |   | Output |
| Search | Endorse | Optional | Button |
| Search | Renew *(only if policy in renewal period)* | Optional | Button |
| Search | Cancel | Optional | Button |
| Search | Actions | Optional | Drop Down list with the following: · Edit · View History - Remove |
| Additional Actions | Button on Search screens |
| Additional Actions | Action Type | Yes | Drop Down |
| Additional Actions | Status | Yes | Drop Down |
| Additional Actions | Note | Yes | Text |
| Additional Actions | Submit |   | Button |
| Additional Actions | Cancel |   | Button |
| Search | **Business Profile** |
| Search | Legal Representative -First Name |   | Output |
| Search | Legal Representative - Position |   | Output |
| Search | Legal Entities -Legal Name *(can be multiple occurrence) * |   | Output |
| Search | Legal Entities Business Name *(can be multiple occurrence)* |   | Output |
| Search | Legal Entities -ABN *(can be multiple occurrence)* |   | Output |
| Search | Legal Entities-Trading Name *(can be multiple occurrence)* |   | Output |
| Search | **Locations *****(can be multiple occurrence)*** |
| Search | Address |   | Output |
| Search | Section Codes *(with each Address there can also be multiple occurrences of section codes)* |   | Output |
| Search | **Preliminary Questions *****(Multiple Occurrences)*** |
| Search | Preliminary Question |   | Output |
| Search | Preliminary Answer |   | Output |
| Search | **Activity Groups** |
| Search | Activity |   | Output |
| Search | Declared |   | Output |
| Search | Total Activities |   | Output |
| Search | **Underwriting Questions *****(Multiple Occurrences per Product)***** ** |
| Search | Underwriting Question |   | Text |
| Search | Underwriting Answer |   | Output |
| View Summary | **Documents *****(multiple occurrences)*** |
| View Summary | Select | Optional | Tick Box |
| View Summary | Type |   | Output |
| View Summary View Summary | Transaction |   | Output |
| View Summary | Created |   | Output |
| View Summary | Actions | Optional | Button |
| View Summary | Email Selected Documents | Optional | Button |
| View Summary | **Sub-limits (*****multiple occurrences)*** |
| View Summary | Coverage |   | Output |
| View Summary | Cover |   | Output |
| View Summary | Excess |   | Output |
| Brokerage | Search Button | Yes | Button |
| Brokerage | Broker Email | Yes | Tick Box |
| Brokerage | Transaction Ref/Journey Code | No | Tick Box |
| Brokerage | Search Button | Yes | Button |
| Brokerage | Name of Insured |   | Output |
| Brokerage | Transaction Ref |   | Output |
| Brokerage | Policy Number |   | Output |
| Brokerage | Policy |   | Output |
| Brokerage | Effective |   | Output – Date format DD Month YYYY |
| Brokerage | Expiry |   | Output – Date format DD Month YYYY Button |
| Brokerage | Action | No | Drop Down List |
| Transfer to another Broker | Action button on broker menu |
| Transfer to another Broker | Client |   | Output |
| Transfer to another Broker | Transaction Ref / Journey Code |   | Output |
| Transfer to another Broker | Policy |   | Output |
| Transfer to another Broker | Status |   | Output |
| Transfer to another Broker | Current Broker |   | Output |
| Transfer to another Broker | Select a broker | No | Drop down |
| Transfer to another Broker | Transfer | No | Button |
| Transfer to another Broker | Close | No | Button |
| Cancel Policy | Action button on broker menu |
| Cancel Policy | Transaction Ref/Journey Code |   | Output |
| Cancel Policy | Policy Number |   | Output |
| Cancel Policy | Product |   | Output |
| Cancel Policy | Occupation |   | Output |
| Cancel Policy | Broker Email |   | Output |
| Cancel Policy | Insured’s Name |   | Output |
| Cancel Policy | Inception Date |   | Output – Date format DD Month YYYY |
| Cancel Policy | Expiry Date |   | Output – Date format DD Month YYYY Button |
| Cancel Policy | Cancellation Effective Date | Yes | Drop Down selections are: ·       Inception Date ·       Today ·       Other |
| Cancel Policy | Other Cancellation Date | Yes if other selected | Date format DD Month YYYY |
| Cancel Policy | Reason for Cancellation | Yes | Drop Down selections are: ·       Business did not go ahead ·       Change in Circumstances ·       Business Ceased ·       Service or claims dissatisfaction ·       Price or affordability ·       Duplicate or replaced policy ·       Underwriting or eligibility decline ·       Nonpayment |
| Cancel Policy | Do Not Refund | No | Tick box |
| Cancel Policy | Additional Comments | No | Text |
| Resources | **Helpful Resources** |
| Resources | Claims PDF Form | No | Button |
| Resources | Discount Codes | No | Button |
| Resources | Product Offering | No | Button |
| Resources | Insurance Policy Wordings | No | Button |
| Resources | Claims Library | No | Button |
| Resources | **Training Videos** |
| Resources | Cyber Insurance Training Video | No | Button |
| Resources | Professional Indemnity Training Videos | No | Button |
| Resources | Management Liability Training Videos | No | Button |
| Resources | Business Pack Training Videos | No | Button |
|   |   |   |   |

### Business Requirements

**MEN-01 — Menu and data visibility enforced server-side by role and brokerage group**

**Detail**

Which menu tabs and client/policy data a broker sees must be enforced in the API/service layer (by role — Broker/Admin/Super Admin — and by the ShowBrokerPoliciesByBrokerageGroup setting), so a broker cannot reach another brokerage's data by direct API call.

**Acceptance Criteria**

**Given **a broker who is not part of Brokerage Group X

**When **they call the client/policy API directly with a Group X identifier

**Then **the API returns an authorisation error rather than the data, regardless of what the UI currently displays.

**MEN-02 — Quotes**

**Detail**

On selecting the Quote button, the user must be taken to a page that allows:

- Start New Quote
- View Current Quotes
- View Expired Quote
- From this page the user must be able to email the quote or duplicate the quote.

**Acceptance Criteria**

**Given **a broker has selected the Quote button

**When **the** **page is rendered

**Then **the user must be able to:

- Start New Quote
- View Current Quotes
- View Expired Quote

*Scenario 2:*

**Given **a broker is on the quotes page

When the broker selects the email link

**Then **a copy of the quote will be mailed to his email address

*Scenario 3:*

**Given **a broker is on the quotes page

**When **the** **broker selects the duplicate quote link

**Then **a duplicate copy of the quote will be created, and he will be able to review the questions and make changes

**MEN-03 — Brokerage Menu Item**

**Detail**

A new button is required to allow users to access all quotes and policies which fall under their brokerage regardless of whom the broker is who is allocated to the case.

**Acceptance Criteria**

**Given **a broker is on the menu page

**When **the selects the button “My Brokerage”

**Then **all** **quotes and policies linked to his brokerage should be displayed.

**MEN-04 — Brokerage Search Criteria**

**Detail**

The user should be able to search on Transaction Ref/Journey Code, Policy Number, Client Name or broker email address for all business in his brokerage. Don’t allow for all brokers in brokerage as will halt system.

**Acceptance Criteria**

[blob:https://outlook.office.com/5bce373f-8d5b-446a-9abb-319deb1e05f9](#)**Given **a broker is on the My Brokerage page

**When **the searches on Transaction Ref/Journey Code, Policy Number, Client Name or broker email address for business that belongs to his brokerage

**Then **the relevant data is displayed.

*Scenario 2:*

**Given **a broker is on the My Brokerage page

**When **the searches on Transaction Ref/Journey Code, Policy Number, Client Name or broker email address for business that does not belongs to his brokerage

**Then **nothing is displayed and an error is returned to the user which reads “No records found”.

**MEN-05 — Brokerage – Order data**

**Detail**

All active quotes and policies should be displayed 1st followed by expired quotes and policies

**Acceptance Criteria**

**Given **a broker is on the My Brokerage page

**When **the** **broker is viewing cases in his brokerage

**Then **active quotes and policies must display before those that are expired.

**MEN-06 — Brokerage Data**

**Detail**

- The user should be able to see the following information on the My Brokerage Enquiry:
- Broker Email Address
- Transaction Ref/Journey Code
- Policy Number (where applicable)
- Policy description
- Insureds name
- Status
- Inception Date
- Effective Date
- Expiry date
- Documents
- Actions

Actions to be included are:

·       Endorse Policy

·       Transfer to another broker

·       Send Certificate

·       Send declaration

·       View Documents

·       Cancel policy

**Acceptance Criteria**

**Given **a broker is on the My Brokerage page

**When **the has made his selection

**Then **the columns of data as per the requirement are displayed.

***Scenario 2:***

**Given **a broker can select actions

**When **he has made the selection Endorse policy

**Then **the system should route him into the quote which is prefilled but which he can change.

***Scenario 3:***

**Given **a broker can select actions

**When **he has made the selection Transfer to another broker

**Then **the system should route him into the Transfer to another broker page on which the current broker details are displayed, and he can select from a drop down another broker in his brokerage to transfer the policy to.

***Scenario 4:***

**Given **a broker can select actions

**When **he has made the selection Send Certificate or Send Declaration

**Then **the system should email the selected document to his email address.

***Scenario 5:***

**Given **a broker can select actions

**When **he has made the selection View Documents

**Then **the system should allow him to see existing documents on the policy and select the one he wants to view.

***Scenario 6:***

**Given **a broker can select actions

**When **he has made the selection Cancel policy

**Then **the system should route him into the Cancel Policy page.

***Scenario 7:***

**Given **a broker wants to cancel a policy

**When **he selects the Cancel policy button

**Then **the Cancel Policy page should display the Journey Code which it is allocating, policy number, product, occupation, broker email, Insured’s name, Inception and Expiry dates. It should then allow the user to enter when the cancellation should be effective, the cancellation reason, refund indicator and any other comments.

**MEN-07 — Referrals**

**Detail**

Currently a broker can select either open or Closed/Expired referrals. Business wants to also be able to select all referrals for the specific broker. The Open Referrals must appear before the Closed Referrals. Once on the My Referral Screen, the user must be able to search for a specific referral by policy number or by client.

**Acceptance Criteria**

**Given **that a broker may want to see all his referrals

**When **the** **user selects “My Referrals”

**Then **he should be given options in the drop-down to select:

- All Referrals
- Open Referrals
- Closed Referrals

*Scenario 2:*

**Given **that the broker has selected to view “All Referrals”

**When **the** **referrals are displayed

**Then **Open referrals are displayed followed by closed referrals

*Scenario 3:*

**Given **that the user may want to view or process the referral

**When **the** **user selects the “Select” button under Actions

**Then **he must be able to:

- “View Details”
- Resume the Quote
- Decline the Quote
- Duplicate the Quote

*Scenario 4:*

**Given **that the broker has selected to view details

**When **the details screen is displayed

**Then **display the Business Profile, Preliminary Questions, Underwriting Questions and details of the referral activity including the comments sent to the insurer and any documentation sent to the insurer 

  


**MEN-08 — Search**

**Detail**

When the user selects the search item on the menu, he must be able to search by:

- Transaction Ref/Journey Code
- Policy Number
- Client Name
- Broker email address

For Brokers the search should only return data for journeys linked to his broker code or for journeys in his brokerage that have shared broker codes. journeys in his brokerage that have shared broker codes. The search should be open to all Transaction Ref/journey codes and all policies for Administrators.

The data returned should provide:

- General Details of the Journey
- Latest Policy Details
- Business Profile
- Preliminary Questions
- Underwriting Questions



The user should be able to copy all policy details so that these can be used for tasks such as referral comments.

Under the Latest Policy Details the user should be able to select to View a Summary. This summary should allow the user to choose documents he wants to view and the Cover present on the policy. 

The Latest Policy Details if selected should display information around cover, Excess, Inception Date, expiry Date, Effective date and Special Circumstances to the broker. If the user is an administrator in addition to displaying these fields, the system should also display sub-limits of Cover and Excess. Ad Administrator should also be able to update Cover and Excess fields. 

The user should also be able to do the following if the policy is active:

- Endorse the policy
- Cancel the policy
- Renew the policy if the policy is in the Renewal period

If the user is an Administrator, he should also be able to add Special Instructions.

 

**Acceptance Criteria**

**Given **that the user has selected the search tab

**When** the** **search box is presented

**Then **the user should be able to search on the following:

- . Transaction Ref/Journey Code
- Policy Number
- Client Name
- Broker email address

*Scenario 2:*

**Given** that brokers may only view data belonging to them or to brokers in their brokerage who have selected to share their data 

**When** the search criteria are entered

**Then** only journeys that belong to the broker and match the search criteria should be returned. 

*Scenario3:*

**Given** that several policies may be returned for one Transaction Ref/Journey Code

**When** the data is returned the user must be able to select which policy he wishes to view

**Then** only display data for the rest of the enquiry based on the policy/policies chosen. 

*Scenario 4:*

**Given** that the broker may want to see documents sent

**When **he selects the view summary button 

**Then** documents related to the policy must be listed and he must be able to select to view the specific document or email the selected document. 

  


*Scenario 5:*

**Given** that the user is an Administrator

**When **he selects the view summary button 

**Then** documents related to the policy must be listed and he must be able to select to view the specific document or email the selected document or regenerate the documents. 

*Scenario 6:*

**Given** that the user is a broker

**When **he selects the policy under Latest Policy Details, 

**Then**. display information around cover, Excess, Inception Date, expiry Date, Effective date and Special Circumstances to the broker.  

*Scenario 7:*

**Given** that the user is an Administrator

**When **he selects the policy under Latest Policy Details, 

**Then**. display information around cover, Excess, Inception Date, expiry Date, Effective date and Special Circumstances. Sub-Limits for Cover and Excess must also be displayed to the Administrator.  

*Scenario 8:*

**Given** that the user is an Administrator

**When **he selects the edit button on Cover or Excess

**Then **he must be able to update these values. 

*Scenario 9:*

**Given** that the user is an Administrator

**When **he selects the edit button next to a Sub Limit 

**Then **he must be able to change the cover or excess for that sub-limit. 

*Scenario10:*

**Given** that the user is a broker

**When **he is viewing Latest Policy Details

**Then **no edit button should be present for Cover and Excess or next to Cover and Excess on Sub-Limits. 

*Scenario 11:*

**Given** that the policy chosen is active

**When t**he user doing the search is an administrator 

**Then** a special instructions button must present which allows him to add special instructions which will freeze the policy. 



**MEN-09 — Renewals **

**Detail**

When the user selects Renewal all renewals which are due in the next 30 days, for the specific broker must be displayed. If he has no renewals due, then a message “No policies are currently ready for renewal.” Must be displayed. 

On each separate renewal there should be an action button. If the policy is a manual renewal, then only a renew action need be displayed and this should route the user to the beginning of the quote process. If the policy is an autorenewal, then the actions that the user should be able to select are:

- Auto Renew
- Edit/Remarket

If Auto Renew is selected the user should be directed straight to the bind process. If Edit/Remarket is selected, then the user must be directed to the beginning of the quote process.

 *Scenario 1:*

**Given** that the Renewal tab is selected

**When t**he user doing the search is a broker 

**Then** all his renewals due in the next 30 days should be displayed. 

*Scenario 1:*

**Given** that the Renewal tab is selected

**When **there are no renewals due for the broker 

**Then** display a message “No policies are currently ready for renewal” 



*Scenario 3:*

**Given** that the policy may only be able to be renewed manually

**When t**he user wants to select an action 

**Then** the only action that should present is “Renew” and this should take the user into the quote process. 

*Scenario 4:*

**Given** that the policy may be auto renewed 

**When t**he user wants to select an action 

**Then** the actions that should present are “Auto Renew” and “Edit/Remarket”. 

*Scenario 5:*

**Given** that the user has selected “Auto Renew”

**When **the user is moved to the next process

**Then** this should take the user into the bind process. 

*Scenario 6:*

**Given** that the user has selected “Edit/Remarket”

**When **the user is moved to the next process

**Then** this should take the user into the quote process. 



**MEN-10 — Resources**

**Detail**

- A list of useful resources must be made available under 2 headings:
- Helpful Resources
- Training Videos
- Each element in the list needs to be able to be accessed by selecting the view button next to the listed item.
- The list of items must be able to be dynamic (i.e. a super admin user must be able to add or delete items from the list of available resources).



**Acceptance Criteria**

**Given **that a broker has selected the Resources tab

**When** the** **broker selects the view button on a specific item

**Then **the appropriate document is displayed.

*Scenario 2:*

**Given **that a super admin user wants to add/delete a resource

**When **the super admin user logs on to the update function

**Then **he can add an additional resource by giving a description and a copy of the resource. He needs also to be able to position it under the correct subcategory of resources.

*Scenario 3:*

**Given **that the super admin user wants to remove a resource

**When **the super admin user selects the delete icon

**Then **the resource will be removed from the list.

**MEN-11 — Account Details**

**Detail**

- The brokers name, address, email address and phone number must be displayed.

- The data shown must match that which has been captured in the Tools portal

** **

**Acceptance Criteria**

**Given **that a broker has selected the Account Details button

**When** the account details page is displayed

**Then **no fields must be modifiable.

**Given **that a broker has viewed the Account Details

**When** he selects the “close” button

**Then **the account details window must be closed.



  


## Customer Details

### Data Requirements

| **Field** | **Mandatory** | **Format** | **Help** |   |
| --- | --- | --- | --- | --- |
| Legal Entity/Insured Name | Yes | Text | Yes | The person or business to be named in the policy. Additional insured names can be added on the Bind & Payment page. |
| Occupation description | Occupation is Mandatory but only one of the 3 methods need be used to retrieve it | Drop Down List |   |   |
| Occupation Web Search | Occupation is Mandatory but only one of the 3 methods need be used to retrieve it | Allow URL to be entered |   |   |
| Occupation Upload Document | Occupation is Mandatory but only one of the 3 methods need be used to retrieve it | Allow upload of document |   |   |
| Policy Inception Date | Yes | Calendar Selection | Yes | Please note that policies start and expire at 4pm local standard time If the insured have a current policy that expires on the 1st of January to ensure he has no gap in cover, select a Start Date of the 1st of January |
| Policy Expiry Date | Yes | Calendar Selection |   |   |
| Enter Address Manually | Address is Mandatory but user can either enter or search | Button |   |   |
| Search for Business Address | Address is Mandatory but user can either enter or search | Enter some text- then select from drop down list | Yes | If the insured has more than one, use the location he currently works out of. |
| Estimated Annual Revenue | Yes | $ hard coded into field User enters whole number -no cents Number -may not be 0 | Yes | This is the estimated total amount of revenue in the next 12 months from all sales and/or services that the insured’s business carries out. If the insured is employed (whether full-time, part-time, or on a voluntary basis), enter the estimated earnings from wages/salaries over the next 12 months for which this insurance policy is intended to cover. |
| No of Employees | Yes | Number -may not be 0 | Yes | If the insured works as a sole trader or are employed (whether full-time, part-time, or on a voluntary basis), please enter 1 in this field. If you engage contractors, please refrain from entering information here; we will address this later in the process. If you employ part-time workers, please calculate the number of full-time equivalent workers using the formula: 1 full-time equivalent worker = (Total part-time hours over 1 week) ÷ 38. |
| Continue |   | Button |   |   |



### Business Requirements

Note: For Broker portal no customer email or phone number is required by Bizcover as these are kept by the broker on his system. We do not contact clients directly – the relationship with the client belongs to the Broker not to Bizcover.

**CUS-01 — Legal Entity/Insured Name flows through to bind-time documents**

**Detail**

The single 'Legal Entity/Insured Name' must populate as the insured's legal entity name / policy holder name on downstream documents (cover letter, certificate, quote schedule), not just be stored against the application.

**Acceptance Criteria**

**Given **a broker enters a Legal Entity/Insured Name on the Customer Details screen

**When **the** **quote is bound and the cover letter is generated

**Then **that exact name appears as the policy holder on the cover letter and certificate of currency.

**CUS-02 — Occupation Search **

**Detail**

A broker/admin must be presented with 3 possible ways of searching for the occupation:

- By Description
- By Website URL
- By uploading a document

The AI Assistant should provide a Conversation Prompt ““Describe the client's business in your own words, or paste their website, or upload their expiring policy schedule or proposal form— I'll pre-fill the occupation, business details and likely products for you to check. You need only select 1 of the 3 methods”.

**Given **the broker wants to supply the client’s occupation 

**When **the UI displays

**      Then **the system provides 3 possible options to make this entry:

- By Description
- By Website URL
- By uploading a document



**CUS-03 — Occupation Search by Description**

**Detail**

- A broker/admin must be able to search for a business occupation to allow for the correct LMI and ANZSIC to be retrieved for the quote.
- An AI assisted occupation search should return suggestions but never auto-select the occupation for the broker.

**Acceptance Criteria**

**Given **the broker is entering an occupation selection

**When **the** **broker enters < 3 characters

**Then **the system does not display any autocompleted suggestions.

*Scenario 2:*

**Given **the broker is entering an occupation selection

**When **the broker enters 3 characters or more

**Then **the system displays autocompleted suggestions for occupation.

*Scenario 3:*

**Given **a broker types a free text business description into the AI-assisted occupation search

**When **AI returns suggestions

**Then **the broker must actively confirm a specific suggestion

**API**

It is assumed that the existing API for searching occupations by query string will be used for this function. The API end point is:

**GET /occupations/autocomplete**

**CUS-04 — Web Search for Occupation**

**Detail**

The user must enter a valid URL. Where a valid URL is entered, the app must show a preview image of the website so that the user can confirm it is the correct URL. If it is the correct website, then AI must read information off the website (particularly the contacts page and footer) to identify possible occupations for the customer which must be displayed as a list.  

**Acceptance Criteria**

**Given **that the user is choosing to enter a URL

**When **he selects the URL icon

**Then **the AI Assistant should display a conversation starter “Tip: To help select the correct occupation, enter a website URL that contains the most information about the insured's business.”



*Scenario 2:*

**Given **that the user is entering a URL

**When **the system evaluates the URL and finds it valid

**Then **a preview image of the website must be displayed so that the user can confirm it is the correct URL



*Scenario 3:*

**Given **that the user is entering a URL

**When **the system evaluates the URL and finds it invalid

**Then **an error must be displayed – “please enter a valid URL”.

**Note: **Aside from surfacing an error for an invalid URL, the system must also show an error for knowledge cases and blacklisted URLs (e.g. LinkedIn profiles)



**CUS-05 — Upload Insurance Document to Ascertain Occupation**

**Detail**

The user attaches an insurance document that is in PDF format and is < or = 10MB

**Acceptance Criteria**

**Given **the user is choosing to upload a document

**When **he selects the upload document icon

**Then **the AI Assistant should display a conversation starter “For the best result, upload a previous proposal form or policy documentation, such as a certificate of currency or insurance schedule”. It should also display a canned prompt “How do you use this document?”.

  

*Scenario 2****:***

**Given**** **the canned prompt ““How do you use this document?” is available

**When**** **he selects the prompt

**Then**** **the AI Assistant should display the following:



**Here's how the document helps:**

Occupation matching - I'll extract details about the insured's r business activities from the document to find the closest matching occupation in our system. Pre-filling the insured's details - If the document contains business information like your company name, address, or contact details, B4B can use those to help fill in the insured's quote form faster.

**What works well:**

Proposal form

Policy Documents such as:

Previous insurance certificates or schedules

Business registration documents

Any document that clearly describes what your business does

**Privacy note: **

The document is only used to extract relevant business information for the insured's quote. B4B won't store or share it beyond that purpose.

Would you like to upload a document, or would you prefer to describe the insured's business in your own words instead?



*Scenario 3****:***

**Given **the system will only accept documents in PDF format that are < or = 10 MB

**When **the user is trying to select documents

**Then **only PDF documents < or = 10 MB should be able to be selected. 



*Scenario4:*

**Given **the user has selected a document to upload

**When **the system has not been able to upload the document

**Then **an error must be returned “Upload failed – *“reason for failure”*, please try again” and the AI Assistant must surface a message “We found that document hard to read, do you have any others documents you can upload?”.



**CUS-06 — AI occupation-recommendation**

**Detail**

Any AI-assisted occupation search (natural-language description occupation suggestions must never auto-select an occupation on the broker's behalf. Every AI suggestion, and whether the broker accepted or overrode it, must be logged to support both compliance review and future model retraining.

**Acceptance Criteria**

**Given** a broker types a free-text business description or selects a URL or attaches a document into an AI-assisted occupation search

**When **the** **AI returns suggestions

**Then **the broker must actively confirm a selection before it is applied.



*Scenario 2****:***

**Given** that AI will make suggestions to the best of its ability

**When** the suggestions are displayed

**Then** simultaneously in the AI Assistant display a pop up “Does this look right to you?” and a conversation starter “If these results aren’t accurate either try another one of the methods or refine your information”.

*Scenario 3****:***

**Given** that AI will make suggestions throughout the quote process

**When** the occupation selection is shown

**Then** an AI disclaimer must be shown with a tick box for the broker to select



  


**CUS-07 — Protection of Personal Information**

**Detail**

The policy Inception Date may only be today’s date or a date up to 30 days in the future when entered by broker

Acceptance Criteria



**Given** that BizCover may not collect Personal Information without client agreement

**When** the 1st quote page is shown 

**Then** a Personal Information Agreement notice must be displayed with a tick box for the broker to select



**CUS-08 — Policy Inception Date Broker**

**Detail**

An agreement to BizCover terms and conditions and privacy policy must be displayed below the AI Disclaimer. This agreement needs to be shown upfront before we collect any personal information.  

**Acceptance Criteria**

**Given **policies may only be current or future dated by the broker

**When **the** **broker selects a date

**Then **dates prior to current date should not be available for selection

*Scenario 2****:***

**Given** that a Broker can quote up to 42 days in advance

**When** the user is entering inception date

**Then** simultaneously in the AI Assistant display “You can quote up to 42 days in advance.”



**CUS-09 — Policy Inception Date Administrator**

**Detail**

The policy Inception Date may be today’s date or a date in the future or a date in the past when entered by an Admin

**Acceptance Criteria**

**Given **policies may be current or future dated or backdated by the Administrator

**When **the** **Administrator selects a date

**Then **dates prior to current date are available for selection

**CUS-10 — Policy Expiry Date**

***Note:**** Expiry date is not provided on the Blaze-X and Agent-X UI.*

**Detail**

The Policy Expiry Date must default to inception date + 1 year but may be any date up to 6 months prior to that date or 6 months after that date.



**Acceptance Criteria**

**Given **that the expiry date can be any date in the period 6 to 18 months forward from current date

**When **the user selects the calendar to enter an expiry date

**Then **all dates between 6 and 18 months from current date should be allowed to be selected. All other dates must be blocked.

*Scenario 2****:***

**Given** that expiry date maybe anything from 3 months to 18months in the future depending on product and insurer

**When** the date is being chosen

**Then** simultaneously in the AI Assistant display a pop up “Our shortest policy period available for this product is X” and a conversation starter “While policy standardly expires after a year - expiry maybe up to Y months in the future.”.



**Note:** The system must determine minimum and maximum expiry dates from a table that will be developed to contain the information provided on the link: <u>**https://bizcover.atlassian.net/wiki/spaces/BFB/pages/4765646851/Minimum+and+Maximum+Policy+Period?atlOrigin=eyJpIjoiZjUyYWY1ZGQ3ZWFkNGQzZGIyNWY0NjllNWRhNTkzMWQiLCJwIjoiYyJ9**</u>



**CUS-11 — Enter Address Manually**

**Detail**

The user must be able to enter the address manually. The same logic as is present on Agent-X applies.

**Acceptance Criteria**

**Given **that “Enter Manually” is a valid selection for entering the address

**When **the “Enter Manually” button is selected

**Then **the following address fields must be presented for entry:

- Street number
- Street Name
- Suburb
- State
- Postcode
- Country
- Unit Number
- Building Name



**CUS-12 — Search for Business Address**

**Detail**

The user must be able to search for the address. Same logic as is present on Agent-X applies.

**Acceptance Criteria**

**Given **that search is a valid selection for entering address

**When **the** **user enters some text

**Then **the system must return options that match criteria (e.g. If the user enters 330 Pitt, then the system must return all address options which have 330 Pitt in them, such as 330 Pitt Street, 330 Pitt Town Road and 330 Pittwater Road should all be displayed for selection)

*Scenario 2:*

**Given** address selected, 

**When** selected, 

**Then** postcode auto-populates



**API**

It is assumed that the existing API for searching addresses by query string and for retrieving detailed address components will be used for this function. The API end points are:

**GET /locations/address/autocomplete**

**GET /locations/address/components**



**CUS-13 — Continue**

**Detail**

All fields on the page are mandatory

**Acceptance Criteria**

**Given **that any field has not been completed

**When **the** **user wants to proceed to the next page

**Then **the continue button must be greyed out and not allow him.



  


## Manual Address

### Data Requirements

| **Field** | **Mandatory** | **Format** | **Help** | **Help Text** |
| --- | --- | --- | --- | --- |
| Street Number | No | Text | No |   |
| Street Name | Yes | Text | No |   |
| Suburb | Yes | Text | No |   |
| State | Yes | Drop Down | No |   |
| Post Code | Yes | Numeric | Yes | This is the postcode of the mailing address, which may differ from the postcode of the insured’s business premises. |
| Country | Yes | Prefill | No |   |
| Unit Number | No | Text | No |   |
| Building Name | No | Text | No |   |



### Business Requirements

**ADD-01 — Enter Address**

**Detail**

The user must be able to select the state from the following drop-down list:

- NSW
- VIQ
- QLD
- WA
- SA
- TAS
- ACTN
- NT

If a valid postal code is entered, then the state should be auto populated. 



**Acceptance Criteria**

**  ****Given **that the Broker/ Administrator is entering the address

** When **an invalid postal code is entered

**  Then **the display an error “Please enter a valid postcode”

** ***Scenario 2:*

** ****Given **that the Broker/ Administrator is entering the address

** When **a valid postal code is entered

**  Then **auto-fill the state

*Scenario 3:*

**Given **that there are only 8 valid states

**When **the** **user wants to enter the state

**Then **the system must supply a drop-down list with valid names.

**Note:** This is currently available on Blaze-X but not on Agent-X

**ADD-02 — Enter Country**

**Detail**

This should be preset to Australia – the user should not have to enter. If at a later stage, we extend business on this Platform to New Zealand then this field should be drop-down.

## Journey Id

When the Broker/Administrator has completed all the preceding questions and selects continue, a journey id is created. If the user selected continue and not all questions had been answered, then the system should display an error and highlight the question that has not been answered.

**Acceptance Criteria**  
**Given** that the Broker/Administrator has completed the preliminary questions  
**When** he selects continue  
**Then** a “Journey Id” must be created and be displayed to the user.  
*Scenario 2:*  
**Given** that the Broker/Administrator has completed the preliminary questions and has selected continue  
**When** the system identifies that a question has not been answered  
**Then** an error message should be displayed “To continue please answer the highlighted questions”.  
*Scenario 3:*  
**Given **that the API cannot produce the Journey ID  
**When** the API returns an error  
**Then **an error message is displayed, and the user is allowed to retry.  
*Scenario 4:*  
**Given** journey < 30 days old,  
**When** the broker exits the case and then resumes it,  
 **Then** he can continue from last step he executed

**API**  
It is assumed that the existing API for creating a new insurance journey with customer and business information will be used for this function.  The API however will need to be altered as for business loaded by brokers only an insured name not a first name and last name are captured. Also, no email or telephone number for the client is captured. The API end point is:

  


## Product

### Data Requirements

| **Field** | **Mandatory** | **Format** | **Help** | **Help Text** |
| --- | --- | --- | --- | --- |
| Public Liability | No | Tick Box | Yes | Public Liability insurance provides protection if someone makes a claim against the insured, the business or its employees. Claims from a third-party can be for personal injury or damage caused to their property caused by your business activities. |
| Cyber Liability | No | Tick Box | Yes | Cyber Liability insurance is designed to help protect the insured from claims and support his profitability in the event of a cyber breach or attack. Costs associated with defending a cyber claim are also covered. Examples of the types of risks Cyber Liability insurance can assist with are inadvertent loss or release of customer personal information, cybercrime, cyber extortion/ransomware and business interruption due to a cyber event. |
| Professional Indemnity | No | Tick Box | Yes | Professional Indemnity (PI) insurance is designed to protect the insured if a client claims that the insured’s professional advice or services caused them a financial loss. As an accountant, this is one of the most important covers the insured can have. |
| Management Liability | No | Tick Box | Yes | Management liability insurance protects directors and officers and the insured company itself from the many exposures relating to the management of a company. |
| Personal Accident & Illness | No | Tick Box | Yes | Personal Accident & Illness insurance covers the insured for loss of income if he is unable to work because of an injury or illness. The cover is generally available regardless of whether he sustains injury or develops an illness due to your work. |
| Bizpack | No | Tick Box | Yes |   |



  


### Business Requirements

**PROD-01 — Product Selection**

**Detail**

The user needs to select at least one of the following cover types:

- Professional Indemnity
- Public Liability
- Cyber Liability
- Management Liability
- Personal Accident & Illness
- Bizpack

**Note:** Agent-X and Blaze-X do not display a Bizpack selection but only a separate list of Bizpack covers. Broker business wants the Bizpack to specifically be shown as a product.



**Acceptance Criteria**

**Given **the user is on the product page

**When **the product page loads 

**Then** products available for the client’s occupation are displayed.

*Scenario 2:*

**Given **the user wishes to select a product 

**When** he selects the tick box

**Then **the tick box is hi-lighted.

*Scenario 3:*

**Given **the user wishes to remove a selection

**When **he unchecks the tick box

**Then **the hi-lighting is removed & the selection will not be passed.

*Scenario 4:*

**Given **the user selects at least 1 product except Bizpack 

**When** he selects continue

**Then **the system will proceed to the Business Details page.

*Scenario 5:*

**Given **the user selects Bizpack

**When **the user selects a specific cover (e.g. glass) 

**Then** he may select the continue button.

*Scenario 6:*

**Given **the user is trained in giving specialist advice

**When **the products are displayed 

**Then** the system must not pre-select products.

*Scenario 7*

**Given **that only products which are available for the occupation are displayed

**When **the products are displayed 

**Then** the Ai Assistant should display a conversation starter ““We have displayed the products available to quote on our platform for the selected occupation"

*Scenario 8*

**Given **the user has completed his selection of products 

**When** if he has not selected all the available products

**Then **the AI Assistant must prompt the user to choose further relevant products by displaying a pop up for the product not chosen “Based on the information provided for risk product X is also available” and a conversation starter “Would you like me give you an indicative quote for X cover?”.

**Note:**** **Marketing is trying to punt the Cyber product thus if the Cyber product is not selected, this prompt should start with the Cyber Product. Further prompts will be supplied by marketing re facts and figures as to why cyber cover is important. ** **







**API**

It is assumed that the existing API used to retrieve available product types for the journey based on customer and business information will be used. Similarly, the existing API for selecting a product type and sections for the journey should also be used.

The API endpoints are: 

**GET /journeys/{journeyId}/product-types**

**PUT /journeys/{journeyId}/product-type-selection**



**PRO-02 — BIZPACK occupation eligibility resolved via insurer-occupation mapping, not industry constraints**

**Detail**

BIZPACK must only be offered as an available product on the Cover Selection screen if the broker's entered business description resolves to an occupation that has a mapped insurer occupation code with at least one of QBE, AIG, or RELYON. If the resolved occupation has no mapped occupation code for any of these insurers, BIZPACK must be excluded from the available products on the Cover Selection screen — regardless of whether the underlying industry code itself is valid.

**Acceptance Criteria**

**Given **a broker enters a business description that resolves to an occupation with no mapped QBE/AIG/RELYON insurer occupation code

**When **they reach the Cover Selection screen

**Then **BIZPACK is not offered as an available product for that business, even though the industry code itself is valid.

**PROD-03 — Bizpack Detailed Menu**

**Detail**

When the user selects Bizpack then an additional list must be displayed with the following:

- Contents
- Theft
- Glass
- Statutory Liability
- Portable Equipment
- Money
- Electronic Equipment
- Goods in Transit
- Building
- Employee Dishonesty
- Machinery Breakdown
- Tax Audit
- Business Interruption



**Acceptance Criteria**

**Given **that Bizpack is made up of multiple cover types

**When **the** **user selects Bizpack

**Then **an additional selection list must be displayed.

- **Note:** The behaviour here is different to Agent-X and Blaze-X who always show this list. For broker the list is only to be shown where Bizpack has been made as a selection.



  


## Activity Split

### Data Requirements

| **Field** | **Mandatory** | **Format** | **Help** | **Help Text** |
| --- | --- | --- | --- | --- |
| Search activities… | No | Free text search | No help icon shown |   |
| Activity % (e.g. Accounting Lecturing, Accounting software programs, Auditing) | No | Numeric % | No |   |
| Sub-activity % (e.g. Listed Public Companies / Financial Institutions, Public Companies Limited by Guarantee) | No | Numeric % | Yes | Allocate the % for each sub activity. Total must equal 100% |



### Business Requirements

**ACT-01 — Revenue Questions**

**Detail**

Answers to revenue questions must sum to 100%

**Acceptance Criteria**

**Given **that an agent is entering revenue percentages

**When **the has entered all percentages

**Then **total revenue must sum to 100%

*Scenario 2:*

**Given **that activities may not all be displayed

**When **activities are displayed 

**Then **the AI Assistant must display “Tip: If insured activities are not listed, you can search for the activity.”



**Note:** Business do not want the percentage to be able to be selected using a slider.



**ACT-02 — Sub Activity for specific revenue type**

**Detail**

Sub-activities for a given activity only expand once a value is entered against the parent activity and collapse again if that value is cleared.  This keeps the list manageable. Answers to sub activity questions for a specific revenue must sum to 100%

**Acceptance Criteria**

** ****Given **that sub-activities make the list very long

**When **a parent activity is selected 

**Then **the list of sub activities is created.

*Scenario 2:*

**Given **that sub-activities may not all be displayed

**When **a parent activity is selected and sub activities are displayed 

**Then **the AI Assistant must display “Tip: If insured sub-activities are not listed, you can search for the sub-activity.”

*Scenario 3*

**Given **that an agent is entering sub activity percentages for a specific revenue

**When **the has entered all percentages

**Then **the total for that type of revenue must sum to 100%

**Note:** Business do not want the percentage to be able to be selected using a slider.

**API**

It is assumed that the existing API used to retrieving preliminary questions will be used. Similarly, the existing API for submitting answers to preliminary/coverage questions should also be used.

The API endpoints are: 

**GET /journeys/{journeyId}/preliminary-questions**

**PATCH /journeys/{journeyId}/preliminary-question-answers**



## Occupation Classification

### Data Requirements

| **Field** | **Mandatory** | **Format** | **Help** | **Help Text** |
| --- | --- | --- | --- | --- |
| Specific Occupation per Insurer | Yes | Dropdown | Yes | Select the closest occupation classification for each insurer. If none match the insured business, choose 'No exact match' — that insurer's product will not be quoted. |

### Business Requirements

**SOI-01 — Specific Occupation per Insurer**

**Detail**

The user must be able to select between different relevant options and no exact match

**Acceptance Criteria**

**Given **that there may be multiple selection of occupations for an insurer 

**When **the occupations are displayed

**Then t**he AI Assistant should display a pop up “Some insurers may have multiple occupation options for the risk you have chosen. Please review and select most relevant”.



*Scenario 2:*

**Given **that a selection of occupations for an insurer is listed

**When **the client’s occupation does not meet any of these

**Then **he must have the option to choose “No Exact Match” for that insurer.



**API**

It is assumed that the existing API used to retrieving preliminary questions will be used. Similarly, the existing API for submitting answers to preliminary/coverage questions should also be used.

The API endpoints are: 

**GET /journeys/{journeyId}/preliminary-questions**

**  PATCH /journeys/{journeyId}/preliminary-question-answers**

## Underwriting

### Data Requirements

### Please view the spread sheet at the link [https://bizcover.atlassian.net/wiki/spaces/BFB/pages/4761485320/Tool+Tips+Help+Messages?atlOrigin=eyJpIjoiNDg4ZDc4YTg3OGQ4NGZkNmJiMDZjYWE4YTBmNDM5MzQiLCJwIjoiYyJ9](https://bizcover.atlassian.net/wiki/spaces/BFB/pages/4761485320)

### This contains all the fields for underwriting, and which fields have tool tips (help) and what hat help is.

### Note: The help text for Broker and Administrator does differ from the current (help)tooltips being provided on BlazeX and AgentX as the audience is different and therefore some wording is not appropriate. 

  


### Business Requirements

### As underwriting questions vary dependent on the client’s occupation, location and products he selects – requirements have not been listed for each individual question but for each type of question.   

**UND-01 — Loading Questions for Each Product**

**Detail**

Questions for each product selected must be added to the list of underwriting questions selected. These should be ordered per product.

**Acceptance Criteria**

**Given **the agent originally selected 1 product

**When **he adds an additional product

**Then **questions for that product are added.

*Scenario 2:*

**Given **the user has selected multiple products (e.g. Personal Indemnity and Public Liability)

**When **the underwriting questions are built

**Then **all questions for the 1 product or displayed followed by all questions for the other product.

**UND-02 — Block Continue**

**Detail**

- All underwriting questions must be answered before the user can proceed to Interested Parties. If he has not answered all questions:
- The continue button should be greyed out
- An error message should be displayed: “To continue please answer the highlighted questions!’
- The unanswered questions should be highlighted
- The AI Assistant should display a pop up showing the number of questions not answered, for example “You have not answered 3 questions.”



**Acceptance Criteria**

**Given **that the user has not completed all underwriting questions

**When **the** **user wants to proceed to Interested Parties

**Then **he cannot until all questions are answered (i.e. Continue button is greyed out and error is displayed)

**UND-03 — Cover Amounts**

**Detail**

Where there are specific cover amounts for a product then these must be displayed as a drop-down list

**Acceptance Criteria**

**Given **that a product has specific pre-defined cover amounts

**When **the user is selecting cover

**Then **a drop-down list of allowed covers should be displayed

*Scenario 2:*

**Given **that sometimes broker business has requests for larger amounts than the pre-defined limits 

**When **a Super Administrator is processing ** **

**Then **allow for an additional selection in the drop-down marked as other, if this is selected show an additional input field where the user can enter an amount.

**UND-04 — Excess Amounts**

**Detail**

Where there are specific excess amounts for a product then these must be displayed as a drop-down list

**Acceptance Criteria**

**Given **that a product has specific pre-defined excess amounts

**When **the** **user is selecting excess

**Then **a drop-down list of allowed excesses should be displayed

  


*Scenario 2:*

**Given **that excesses are specific to a cover

**When **excess is changed for that cover

**Then **only the calculations related to that cover and the total premium should change.

**UND-05 — Yes/No Questions**

**Detail**

Answers to Yes/No questions must always be Yes or No

**Acceptance Criteria**

**Given **that an agent is answering Yes/No question

**When **answering

**Then **he must select either “Yes” or “No”

**UND-06 — Percentage Questions**

**Detail**

Certain product specific underwriting questions include percentages in the answers

**Acceptance Criteria**

**Given **that the questions ask for percentages

**When **answering requires answers to total to 100%

**Then **an error must be displayed if the answers do not total 100%

**UND-07 — ****Error Processing**

**Detail**

As there are many underwriting questions, if the user gets to the end of the underwriting questions and he has skipped a question when he selects to continue an error message should be displayed and any question he has missed should be highlighted. 

**Acceptance Criteria**

**Given** that a user may not have answered all questions

**When** he selects the continue button

**Then** an error must be displayed “To continue please answer the highlighted questions”.

**UND-08 — AI Assistant**

**Detail**

As the bulk of underwriting questions are linked to product rules which may be complex and too detailed to put in a help (tool tip), the AI Assistant should be able to take a free-text question from the broker and give a relevant answer from information stored on the AI Platform.   

**Acceptance Criteria**

**Given** that a user may need complex questions answered 

**When** the user asks a free format question of the AI Assistant

**Then** the AI Assistant must use documentation stored on its platform to answer these questions.  



*Scenario 2:*

**Given** that the AI Assistant has a limited amount of knowledge 

**When** the user asks a free format question the AI Assistant cannot answer

**Then** the AI Assistant must return the message to the broker “I cannot answer your question, please contact Bizcover @ 1300 295 262.” Or if an administrator is the user “I cannot answer your question”   



**API**

It is assumed that the existing API used to retrieving underwriting questions will be used. Similarly, the existing API for submitting answers to underwriting questions should also be used.

The API endpoints are: 

**GET /journeys/{journeyId}/underwriting-questions**

**  PATCH /journeys/{journeyId}/underwriting-question-answers**

## Bizpack

### Data Requirements

| **Field** | **Mandatory** | **Format** | **Help** | **Help Text** |
| --- | --- | --- | --- | --- |
| Statutory Liability | No | Checkbox | Yes | Statutory Liability insurance protects the insured, his business and his employees against certain unintentional breaches of some Australian laws. It also covers the costs of representation related to investigation costs for alleged breaches, as well as defence costs, and fines or penalties payable following a conviction. |
| Portable Equipment | No | Checkbox | Yes | Portal Equipment insurance (also known as General Property insurance) covers the insured for loss and damage to items of portable equipment associated with his business. These can include tools of trade and items of stock. |
| Contents | No | Checkbox | Yes | Covers the insured’s business contents or stock if they were damaged in a fire, storm or due to malicious damage or some other defined event listed in the policy. |
| Theft | No | Checkbox | Yes | This option can cover the insured’s contents and stock from theft, attempted theft or armed hold up. It is not uncommon for theft insurance to require the item stolen to have been securely stored before the theft and for there to be evidence of forcible entry in the commission of the theft. |
| Glass | No | Checkbox | Yes | Glass insurance provides cover for breakage of internal and external glass and signage belonging to the insured or for which he is legally responsible, at the insured premises. |
| Tax Audit | No | Checkbox | Yes | Tax Audit Insurance covers a business for specified costs if it is selected by the Australian Tax Office for auditing. The policy covers the costs of accountants and other professional fees incurred during an audit. |
| Goods In Transit | No | Checkbox | Yes | Goods in Transit covers (subject to a specified limit) loss or damage to goods owned by the insured which are damaged in transit by road in Australia and caused by insured events such as collision, fire, flood or theft by forcible entry. |
| Building | No | Checkbox | Yes | Building Insurance covers the insured’s building if it is damaged by an insured event, such as fire, storm, malicious activity or other event as defined by the policy. |
| Business Interruption | No | Checkbox | Yes | Business Interruption insurance provides cover for the loss of income and increased costs of operating the insured’s business caused by a specified insured event (such as property damage or fire). It’s designed to assist the insured’s business to recover from an insured event by paying ongoing expenses (such as wages or rent). |
| Money | No | Checkbox | Yes | Money insurance protects the insured’s business money (which will include not only cash and cheques, but also items such as lottery tickets, gift cards, postal orders and stamps) by providing cover for loss or damage to it whilst on the insured’s premises or in transit. |
| Electronic Equipment | No | Checkbox | Yes | Electronic equipment insurance covers the cost to repair or replace specified electronic equipment following a breakdown. The insured can also choose to insure, the additional costs to his business or business interruption expenses caused by a breakdown of electronic equipment. |
| Machinery Breakdown | No | Checkbox | Yes | This insurance covers the cost to repair or replace specified machinery following a breakdown. |
| Employment Practices Liability | No | Checkbox | Yes | Employment Practices Liability insurance is designed to cover a company from claims made by employees in relation to their employment conditions or breaches of employment laws. This can include claims arising from unfair dismissal or discrimination. |
| Employee Dishonesty | No | Checkbox | Yes | Covers the insured’s business for losses incurred by theft, fraudulent or dishonest acts by his employees, subject to obtaining Money and / or Contents insurance. |



  


### Business Requirements

**BIZ-01 — Bizpack Dependency Rules**

**Detail**

BIZPACK sections have mandatory prerequisite sections for certain insurers (e.g. for AIG: Building/BI/Theft/Money/EE/MBD each require Content; Glass/PE require Content or PL). If these prerequisite sections are not selected, then the system must not quote for those sections for that insurer. Similarly, if certain clause codes (specific to QBE) exclude an occupation then the quote should not be produced for Bizpack for QBE.

**Acceptance Criteria**

**Given **a broker has not selected a pre-requisite cover for an insurer

**When **the** **calculation engine runs the quote

**Then **no Bizpack quote should be produced for that insurer



## Interested Parties

### Data Requirements

| **Field** | **Mandatory** | **Format** | **Help** | **Help Text** |
| --- | --- | --- | --- | --- |
| Do Interested parties need to be noted on this policy? | Yes | Yes/No Buttons | Yes | You are unable to include additional insured parties by adding them as an interested party. |
| Name of Interested Party | Yes | Text | No |   |
| Nature of Interest | Yes | Drop-down | No |   |
| Insured’s Address | Yes | Text | No |   |
| Policy Section | Yes | Tick Box for each section | No |   |
| Add Interested Party | Yes | Button | No |   |
| Remove | No | Button | No |   |



### Business Requirements

**INT-01 — Nature of Interest**

**Detail**

The dropdown for Nature of Interest contains the following:

- Franchisor,
- Hire Purchase,
- Landlord,
- Lease,
- Local Government Authority,
- Mortgagee,
- Premium Funder,
- Principal,
- Other,
- Lender



  


**Acceptance Criteria**

**Given **that the user has added an interested party

**When **the** **user selects Nature of Interest

**Then **the list of valid interested parties must be displayed

*Scenario 2:*

**Given **that the user has added an interested party

**When **the list of Nature of Interest is displayed 

**Then also **display an AI Conversation point “If the Nature of Interest is not listed, select other and contact the service team.”



**INT-02 — Insured Address**

**Detail**

The use must be given the opportunity to select the address that is already on the policy or to add another address

**INT-03 — Add Interested Party**

**Detail**

When the user selects this button then all details for the interested party must be saved and a new blank set of details displayed so a further interested party can be entered if necessary

**Acceptance Criteria**

**Given **that the user has entered all required fields

**When **the** **user selects Add Interested Party

**Then **the details which have been entered must be saved & the system must give the user the opportunity to enter a further interested party.

**INT-04 — Policy Sections**

**Detail**

The system must automatically display all policy sections for which an interested party can be selected. Each of these should have a tick box that the user can select if the interested party is relevant to that cover.

**Acceptance Criteria**

**Given **that the user has selected to add an interested party

**When **the** **page displays

**Then **a tick box for each policy section must appear for each policy section where interested parties are relevant and the user must be able to select 1 or many of these sections.



**INT-05 — Remove Interested Party**

**Detail**

The user must be able to remove an interested party that has been added.

**Acceptance Criteria**

**Given **that an interested party has been added

**When **the** **user wants to remove the interested party

**Then **he should be able to select the “Remove” button and the interested party should be removed from the quote.



**API**

It is assumed that the existing API used to save or update interested parties that need to be noted on the policy will be used. 

The API endpoint is: 

  **PUT /journeys/{journeyId}/interested-parties**



  


## Get Quote

### Business Requirements

**GET-01 — Quote API**

**Detail**

On selection of the “Get Quote” button – the system must call the Quote API.

**Acceptance Criteria**

**Given **that a user has selected the “Get Quote” button

**When **the** **button is selected

**Then **the quote API must be called.

*Scenario 2:*

- **Given **that the API fails
- **When **the system receives an error
- **Then **the displays an error message with a retry button.



**GET-02 — Quote Informational**

**Detail**

The page has a display showing how many products are being quoted on, what the progress of the quotations are and how many insurers were ultimately unavailable

**Acceptance Criteria**

**Given **that it may take some time for insurers to return quotes

**When **the Get Quote button has been selected

**Then **the output screen which will show the quote outputs must contain an informational which

- changes as quotes are processed by the various companies.
- Examples
- 3 products on this journey · 2 insurer unavailable
- Finalising Quotes – 1 insurer still quoting



**GET-03 — Quote is not successful for an insurer**

**Detail**

The page displays companies for which a quote could not be returned

**Acceptance Criteria**

**Given **that unsuccessful quotes have been returned

**When **the** **quotes are displayed

**Then **the following information must be displayed to the user for companies that did not return a quote:

- Company Logo
- Product Being Insured
- Error Message from Insurer
- Product that was not quoted on

**Note: **If the error message returned by the insurer is too technical, the AI Assistant should be converting this to a message that can be understood by business.  

*Scenario 2*

**Given **that unsuccessful quotes have been returned

**When **the** **quotes are displayed

**Then **a button must be present labelled “Activity Group Details”

*Scenario 3*

**Given **that the user needs to know the risk appetites of the different insurers for activities quoted on

**When **the quote is rejected &** **the button “Activity Group Details” is selected

**Then **the activities and percentages selected for the quote and the** **risk appetite for each insurer for each activity must be displayed.

**GET-04 — Postal Code for which Quote is selected is embargoed**

**Detail**

Embargo validations need only be invoked for New Business Quotes. System must block quoting/binding for any postcode on an active embargo list, for the specific insurer, product and cover type affected. The embargo check must run per coverage section (Content, Building, Business Interruption) during the rating phase, inside each insurer's quote logic— if a section is embargoed, that section is dropped with no price returned, rather than blocking the whole quote.

  


**Acceptance Criteria**

**Given **that an embargo is present on a postal code for a particular insurer

**When **the** **quote is executed then no price for that product is returned for that insurer and an error should be displayed: “The insured’s circumstances appear to be more unique than most please contact Bizcover @ 1300 295 262”

**Then **the following



**GET-05 — Quote is Successful**

**Detail**

The API returns one or more calculated quotes

**Acceptance Criteria**

**Given **that a successful quote / quotes has/have been returned

**When **the** **quote/s is/are displayed

**Then **the following information must be displayed to the user:

- Company providing Quote
- Product Being Insured
- Comment stating if the quote is Bindable
- Annual Premium
- Number of Sections
- Button to show more details
- Select Button

*Scenario 2:*

**Given **that the user may need more information

**When **the user selects to see more details

**Then **the following information must be displayed:

- Product Cover and Excess
- Endorsements
- Occupation Insured
- Limit of Indemnity
- Policy Cost
- Limit Type
- Sub-Limit of Indemnity
- Reinstatements
- Excess
- Excess Type
- Retroactive Date
- Territorial/Jurisdictional Limits
- Security
- Button to View Policy wording
- Button to view Policy Schedule
- Button to see fewer details



*Scenario 3:*

**Given **that there may be many successful quotes

**When **the quote output is built

**Then **the headline information for each quote should be displayed as an entry on a table.

*Scenario 4:*

**Given **that the Broker/Administrator may want to compare details on the different quotes 

**When **the user selects a button “Compare Quote Details”  

**Then **the system displays a detailed side by side comparison of the quotes from different insurers

 including:

- Insurer logo,
- Price,
- Cover,
- Excess,
- Premium Breakdown
- Sub-limits,
- Exclusions,
- Endorsements,
- Policy Wording link for each insurer

*Scenario 5:*

**Given **that the user has completed viewing the comparison data

**When **the user selects a “close” button 

**Then** he is returned to the quote selection page.

*Scenario5:*

**Given **that the quote comparison data is very detailed

**When **the comparison data is built

**Then** the AI Assistant should generate a short narrative summary calling out the material differences between the returned quotes, so the broker can move to a client recommendation faster than reading every row of every column. 



**GET-05 — Email Quote **

**Detail**

The Broker may want to email the quote to himself or to the client. There thus should be a button on the specific quote that activates the email functionality.  The email functionality 

**Acceptance Criteria**

**Given **that a successful quote / quotes has/have been returned

**When **the** **quote/s is/are displayed

**API**

It is assumed that the existing API used to generate insurance quotes will be used. 

The API endpoint is: 

**POST /journeys/{journeyId}/offers**



## Selected Quote

### Business Requirements

**QUO-01 — Selected Quote**

**Detail**

On selection of a specific quote details of that quote must display in a “Selected Quotations” window

**Acceptance Criteria**

**Given **that a user needs to confirm details of the quote chosen

**When **the** **select button is activated

**Then **the following Quote Details must be displayed:

- Base premium
- Stamp Duty
- Emergency Service Levy
- Agency Fee
- Platform Fee
- Total GST
- Total Premium
- Commission Percentage

**API**

It is assumed that the existing API used to Select a quotation for binding will be used. 

The API endpoint is: 

  **PUT /journeys/{journeyId}/quotation-selection**

**GET-02 — Email Quote **

**Detail**

The Broker may want to email the quote to himself or to the client. There thus should be a button on the selected quote that activates the email functionality.  

**Acceptance Criteria**

**Given **that a successful quote / quotes has/have been returned

**When **the** **quote/s is/are displayed

    **Then **an email button should be available for the user to email the quote. The quote should be sent to the broker who loaded the case.

## Premium Adjustment

### Data Requirements

| **Field** | **Mandatory** | **Format** | **Help** |
| --- | --- | --- | --- |
| Quoted Base Premium |   | Prefilled output |   |
| Adjusted Base Premium | No | Decimal | No |
| Quoted Stamp Duty |   | Prefilled output |   |
| Adjusted Stamp Duty | No | Decimal | No |
| Quoted GST |   | Prefilled output |   |
| Adjusted GST | No | Decimal | No |
| Quoted Platform Fee |   | Prefilled output |   |
| Adjusted Platform Fee | No | Decimal | No |
| Quoted Platform Fee GST |   | Prefilled output |   |
| Adjusted Platform Fee GST | No | Decimal | No |
| Quoted Total Payable |   | Prefilled output |   |
| Adjusted Total Payable |   | Derived from other adjusted fields -output | No |
| Quoted Excess |   | Prefilled output |   |
| Adjusted Excess | No | Number | No |
| Quoted Commission |   | Prefilled output |   |
| Adjusted Commission |   | Decimal - Percentage | No |
| Property Value Under Insureds Care Custody or Control Limit | No | Number | No |
| Reason for Adjustment | Yes | Drop-Down List | No |
| Authority | Yes | Drop-Down List | No |
| Case Number | Depends on value of Authority | Text | No |
| Cancel |   | Button |   |
| Save Adjustment |   | Button |   |



### Business Requirements

**ADJ-01 — Broker Adjustments**

**Detail**

Brokers should only be able to edit their own commission/fee on a quote — all other quote fields should be locked and editable only by BizCover admin users

**Acceptance Criteria**

**Given **a broker is making an adjustment

**When **the wants to change details

**Then **the only field he can alter is the commission

**ADJ-02 — Administrator Adjustment**

**Detail**

Admin User should be able to adjust all fields

**Acceptance Criteria**

**Given **an Administrator is making an adjustment

**When **the wants to change details

**Then **all** **fields can be altered.

**ADJ-03 — Reason for Adjustment**

**Detail**

The Administrator is required to select a reason for the adjustment

**Acceptance Criteria**

**Given **that the Administrator is required to enter an adjustment reason

**When **the user selects the drop down

**Then **the following options must be available:

- Price Match
- Renewal Rollover
- Insured Agreed Premium Edit – Thresholds
- Insured Agreed Premium Edit – Occupations
- Run-off Cover
- Promotional
- Discount
- Multi Policies – Monthly Fee

**ADJ-04 — Authority**

**Detail**

The user is required to choose who is giving authority for this adjustment

**Acceptance Criteria**

**Given **that an adjustment cannot be made without authority

**When **the** **user is entering the authority field

**Then **he must select either Bizcover or Insurer

**ADJ-05 — Case Number**

**Detail**

When Insurer is entered as the authority then a case number must be supplied.

**Acceptance Criteria**

**Given **that the authority chosen is insurer

**When **no value is entered under case number

**Then **an error message must be displayed: “A case number is required When the authority is ‘Insurer’.”

  


**ADJ-06 — Save Adjustment**

**Detail**

When the user selects “Save Adjustment” then the system must recalculate the total premium for the quote

**Acceptance Criteria**

**Given **that changes need to result in a recalculation of premium

**When **the** **user selects “Save Adjustment”

**Then **the total premium must recalculate



**ADJ-07 — Cancel Adjustment**

**Detail**

The user must be able to de-select/revert changes he has made and not store them to the data base.

**Acceptance Criteria**

**Given **that the user can change his mind and decide not to make an adjustment

**When **the** **user selects Cancel

**Then **the window closes & no changes are stored

**ADJ-08 — Audit Note**

**Detail**

When the adjustment has been made – the AI Assistant should create a short summary of the Adjustment (i.e. what changed and who made the change). The user will then accept the note which will then be stored against the policy. This stored note should be available when the user enquires on the policy via BrokerX.   

**Acceptance Criteria**

**Given **that an adjustment has been made

**When **the adjustment** is saved**

**Then **AI must create a brief note detailing what was changed.



**API**

It is assumed that the existing API used to save manual premium adjustments will be used. 

The API endpoint is: 

**     PUT /journeys/{journeyId}/premium-adjustments**

  


## Endorsements

### Data Requirements

| **Field Name** | **Mandatory** | **Format** | **Help** |
| --- | --- | --- | --- |
| Search Endorsement by name or ID | No | Text | No |
| Applied to Policy Number |   | Output |   |
| Applied to Policy Id |   | Output |   |
| Applied to Policy Description |   | Output |   |
| Applied to the Policy -Wording |   | Button | No |
| Applied to Policy – Added Tick box |   | Tick box | No |
| Available to Add Number |   | Output |   |
| Search Endorsements |   | Text |   |
| Available Endorsement – Add Button | No | Button | No |
| Available Endorsement ID |   | Output |   |
| Available Endorsement Description |   | Output |   |
| Available Endorsement-Wording |   | Button | No |
| Available Endorsement – Add Tick box |   | Tick box | No |
| Cancel | No | Button | No |
| Save | No | Button | No |



### Business Requirements

**END-01 — Add Optional Endorsement**

**Detail**

- The Administrator needs to be able to add optional endorsements before binding the policy so that additional clauses, extensions or modifications based on industry will reflect on the quote.
- A list of available endorsement should be displayed from which the user must be able to select an endorsement.
- As the list of available endorsements may be long the user should also be able to search using a keyword such as occupation.
- Once selected, the Administrator should be able to save the endorsement to the quote.
- If the Administrator decided not to add an endorsement, he should be able to cancel out of the page.
- Mandatory endorsements are added automatically & are not part of this functionality.
- Brokers cannot add their own endorsements thus the Endorsement icon should not be displayed to them.



**Acceptance Criteria**

**Given **that the Administrator needs to be able to add additional clauses, extensions or modifications based on industry when a quote is returned

**Then **a button which opens a function to add endorsements to the quote must be available.

*Scenario 2:*

**Given **that the Administrator has selected to add an endorsement

**When **the** **endorsement window opens

**Then **a list of applicable endorsements should appear.

*Scenario 3:*

**Given **many endorsements may be present

**When **the** **list is displayed

**Then **the user must be able to enter text to search for a particular endorsement.

*Scenario 4:*

**Given **that the endorsement needs to be added to the quote

**When **the “Add” tick box is selected and the “Save” button is selected

**Then **the endorsement is added to the quote and displayed online as added to the policy.

*Scenario 5:*

**Given **that the user may decide not to add any endorsement

**When **the selects the “Cancel” button

 **Then** the endorsement window must be closed.

*Scenario 6:*

**Given **an endorsement may have been added in error

**When **endorsements display in the “Applied to this policy” column

**Then **the user must be able to untick the ‘Added” button and select “Save” which will delete the endorsement off the policy.

**API**

It is assumed that the existing API used to save the selected endorsements for the journey will be used. 

The API endpoint is: 

  **PUT /journeys/{journeyId}/endorsements**



## Bind Policy

The Bind Policy page consists of various

**BIN-01 — Bind Policy**

**Detail**

The Bind Policy page consists of various elements or subpages:

- Policies Summary
- Payment Frequency
- Payment Summary
- Contact
- Legal Entities
- Refer Quote
- Legal Representative
- Confirm
- **Note:** While on Agent-X Payment Details are also part of this, for Broker Portal this will not be required as payments are made via the Broker’s commission account.





**Acceptance Criteria**

**Given **that the user needs to confirm information and get client approval

**When **the user accesses the Bind Policy page

**Then **the following sections need to be present:

- Policy Summary
- Payment Frequency
- Payment Summary
- Legal Entities
- Legal Representative
- Confirm - Acknowledgement



*Scenario 2:*

**Given **that for Broker business no client contact details are stored by Bizcover

**When **the** **page is presented

**Then **no Contact section is required

*Scenario 3:*

**Given **that for Broker business no payments are received directly from the client

**When **the** **page is presented

**Then **no Payment Details section is required

## Policies Summary

### Data Requirements

| **Field Name** | **Format** |
| --- | --- |
| Number Policies | Output |
| **Per Policy** |
| Logo | Output |
| Product | Output |
| Sections | Output |
| Cover | Output |
| Excess | Output |
| Insurer | Output |
| **Insured Business** |
| Location | Output |
| Section/s not covered | Output |
| Product | Output |
| Cover | Output |
| Excess | Output |



### Business Requirements

**SUM-01 — Content**

**Detail**

The policies Summary must show how many policies will be created.

The Policies Summary must provide the following information for each policy:

- Insurer Logo
- Product for which insurer is providing Cover
- Sections covered in policy
- Cover
- Excess
- Name of insurer
- For each location the policy is covering the following information must be supplied.
- Location Address
- Products not covered
- Product Covered, Cover and Excess for that specific location



**Acceptance Criteria**

**Given **that the client’s cover may involve various policies from various insurers

**When **the Policies Summary is shown

**Then **details for each policy must be displayed.

*Scenario 2:*

**Given **that the insured may be covered at various locations

**When **the** **policy summary is shown

**Then **the address, product, cover and excess at each location must be displayed.



## Legal Entities

### Data Requirements

| **Field Name** | **Mandatory** | **Format** |
| --- | --- | --- |
| Add Legal Entity | Yes | Button |
| Legal Name | yes | Text |
| ABN | No | Text |
| Business Trading Name is the same | No | Tick Box |
| Business Trading Name | No | Text |



### Business Requirements

**LEG-01 — ABN Length**

**Detail**

The field must be 11 digits long

**Acceptance Criteria**

**Given **the ABN number must be 11 digits long

**When t**he ABN number entered is shorter or longer

**Then **display an error “Please enter a valid 11-digit ABN”

**LEG-02 — ABN Search**

**Detail**

The user searches for the exact business name by entering the ABN

**Acceptance Criteria**

**Given **the ABN number is entered

**When t**he ABN number is found

**Then **the Legal Entity name is auto populated 



**LEG-03 — Business Trading Name is the same**

**Detail**

- If the user selects “Business trading name is the same”, the field “Business Trading Name” should be hidden.
- If it is not selected, then Business Trading Name becomes compulsory.



**Acceptance Criteria**

**Given **that a Business Trading Name is required

**When **the** **name is not the same as the Legal Name

**Then **a Business Trading Name must be entered. If not entered when update is selected display “Business Trading Name is required”.

*Scenario 2:*

**Given **that a Business Trading Name is required

**When **“Business Trading Name is same” is selected

**Then **hide the “Business Trading Name” field.



**LEG-04 — Add Legal Entity**

**Detail**

Multiple Legal Entities may be personas on a policy. Each time the user selects the “Add Legal Entity” button a new occurrence of the Legal Entity fields must be displayed for entry.

**Acceptance Criteria**

**Given **that there may be multiple Legal Entities on a policy

**When t**he user selects the “Add Legal Entity” button

**Then **a new set of the fields Legal Name, ABN, Business Trading Name is the same and Business Trading Name must appear for the user to enter.



**API**

It is assumed that the existing API used to save or update legal entities that will be covered under the policy will be used. 

The API endpoint is: 

  **PUT /journeys/{journeyId}/legal-entities**

### Acknowledgements

| **Field Name** | **Mandatory** | **Format** |
| --- | --- | --- |
| Full Name | yes | Text |
| Position | yes | Text |
| Agreement Term 1 | yes | Tick-box |
| Agreement Term-2 | yes | Tick-box |

### Business Requirements

**REP-01**

**Detail**

The full name and position of the person binding the policy on behalf of the insured the insured needs to be entered.   

**Acceptance Criteria**

**Given **the full name has **not** been entered

**When **the position is entered

**Then **the save button must remain greyed out

*Scenario 2:*

**Given **the full name has been entered

**When **the position is **not** entered

**Then **the save button must remain greyed out

*Scenario 3:*

**Given **the full name has been entered

**When **the position is entered

**Then **the save button must be high lighted

*Scenario 4:*

**Given **the full name entered should be a valid name

**When **less than 2 names (i.e. a name and surname) are entered

**Then **the error “Please enter a valid name and surname” must be displayed 

  


*Scenario 5:*

**Given** acknowledgement section, 

**When** Agreement Terms unchecked, 

**Then** cannot Submit;

*Scenario 6:*

** Given** all fields complete, 

**When** Agreement Terms checked, 

**Then** can proceed



**API**

It is assumed that the existing API used to save or update the details of the person who is acknowledging the terms of business on behalf of the customer. will be used. 

The API endpoint is: 

  **PUT /journeys/{journeyId}/legal-representative**



## Referral to Insurer

### Data Requirements

| **Field Name** | **Mandatory** | **Format** |
| --- | --- | --- |
| Manual Referral | No | Tick Box |
| Reason for Referral | Yes | Drop-down list |
| Comments | Yes | Text |
| Document | No | Allow Upload of Document |
| Document Type | Only if sending document | Drop-down list |
| Submit |   | Button |



### Business Requirements

**REF-01 — Referral Comments**

**Detail**

The referral comments field size needs to be increased from its current 720-character size

**REF-02 — Manual Refer**

**Detail**

If a Vero and QBE policy has been chosen, the user should be able to affect a manual referral to the insurer.

**Acceptance Criteria**

**Given **that the user has selected a QBE or Vero quote

**When **the** **user is on the bind page

**Then **a Refer Quote to Reinsurer block with a Manual Refer tick box should appear.

**REF-03 — Referral Reasons**

**Detail**

Reason for Referral – this should be a drop-down list containing the following reasons:

- Pricing Clarification
- Premium Adjustment
- Commission Adjustment
- Net Rating Required
- Cover Adjustment
- Policy Clauses Query
- Verify Occupation
- General Page Note
- Interested Party
- Change of Expiry Date
- Consideration for No Claim Bonus Adjustment
- NSW Small Business SD Exemption
- Financial Hardship Covid 19
- Other





**REF-04- Document Type**

**Detail**

If a document is attached to the referral, then the document type must be able to be selected.

**Acceptance Criteria**

**Given **that certain insurers require the type of document which is being sent

**When **a document is attached 

**Then **a document type must also be selected.

## Payment Frequency

### Data Requirements

| **Field Name** | **Format** |
| --- | --- |
| Payment Frequency | Output |
| Annual Premium | Output |



### Business Requirements

**FRE-01 — Payment Frequency**

**Detail**

Under payment frequency only the annual payment need be displayed as the business requirement for broker portal is to only offer annual payment policies.

**Acceptance Criteria**

**Given **that only annual frequency is offered on the Broker platform

**When **the** **Payment Frequency is displayed before bind

**Then **only a frequency of annual and the annual premium must be displayed.



**API**

It is assumed that the existing API used to calculate the premium will be used. It must be noted that only annual premium calculation will be required for business sold by brokers. 

The API endpoint is: 

   **POST /journeys/{journeyId}/payment-plans/calculate**

  


## Payment Summary

### Data Requirements

| **Field Name** | **Mandatory** | **Format** |
| --- | --- | --- |
| Base Premium |   | Output |
| Base premium GST |   | Output |
| Stamp Duty |   | Output |
| Platform Fee |   | Output |
| Platform Fee GST |   | Output |
| Total Amount |   | Output |
| Commission Percentage |   | Output |
| Broker Fee | No | Input |



### Business Requirements

7. Integration Requirements

**PAY-01 — Payment Amounts**

**Detail**

Under payments the fields listed above must be displayed. No Card Fee or Card Fee GST must be displayed as all payments for policies sold by the broker channel are paid via the broker’s commission account.

**Acceptance Criteria**

**Given **that payment for policies sold via the broker portal are paid via broker commission accounts

**When **the Payment Summary is displayed

**Then **no Card Fee or Card GST should be displayed.

**PAY-02 — Broker Fee**

**Detail**

- The user must be able to enter a Broker Fee. This must be a $ and cents amount.
- The Broker Fee must be added to the Total premium.



**Acceptance Criteria**

**Given **that a broker can select to be paid a broker fee 

**When** the payment summary is displayed

**Then **the broker must be given the opportunity to enter a broker fee which will be added to the total premium.

**PAY-03 — Multiple Descriptions**

**Detail**

Multiple policies may have been selected thus on the payment summary if there is more than 1 policy involved the items on the payment summary must be subscripted by the product type. An example is if the user has selected both PL and PI then the entries on the payment summary for Base Premium must reflect as Base Premium PI and Base Premium PL  



**Acceptance Criteria**

**Given **that multiple policies may have been sold

**When** the payment summary is displayed

**Then **the entries on the payment summary must be prefixed by the product type.

## Policy Bound

## Data Requirements

| **Field Name** | **Mandatory** | **Format** |
| --- | --- | --- |
| Type of Insurance |   | Output |
| Insurer |   | Output |
| Policy Number |   | Output |
| Effective Date |   | Output |
| Premium Paid |   | Output |
| View Policy Detail | No | Button |
| New Business Journey | No | Button |
| Confirmation Email Sent |   | Output |
| Alternative Email | No | Text |

**BOU-01 —Policy Summary**

**Detail**

The user must be able to see the basic details of the policy on the screen so that he can communicate these to the client.



**Acceptance Criteria**

**Given **that a broker needs to immediately be able to see that a policy has been bound & communicate this to the client

**When** the “Policies bound successfully!” page is displayed

**Then **the following information must be displayed:

- Type of Insurance
- Insurer
- Policy Number
- Effective Date
- Premium Paid
- View Policy Details



**BOU-02 —View Policy Details **

**Detail**

The user must be able to see the full details of the policy when he selects the button “View Policy Details”



**Acceptance Criteria**

**Given **that a broker has entered information supplied by the client to create the policy

**When** the Policy is bound and the “View Policy Detail” button is selected

**Then **the following information sections must be displayed:

- Journey Information
- Latest Payment Summary
- Latest Policy Details
- Business Profile
- Preliminary Questions
- Underwriting Questions
- Activity Group

**Note 1: **The information on these sections must be formulated in the same way they are for Agent-X except for “Latest Payment Summary”. The Payment Summary must only include the Payment Frequency and the Total Payment (Inc. Fees) as payments are made directly to the broker not to Bizcover.  
**Note 2: ** Contact information which is present on Agent-X does not get captured for Broker Business thus this section should not be displayed. 

**BOU-03 — Alternative Email**

**Detail**

The user must be able to add an alternate email address to which the policy details can be resent. This is required because often at a brokerage, the broker who is on record for the client may not be the person who is finalising the request. For example: a quote was requested last week and then referred to the insurer. The broker who requested the quote is now on leave and another person at the brokerage binds the policy when the referral is accepted by the insurer.  

When an alternate email address is used, the AI assistant offers to draft a short covering note giving that recipient the context they need — what was quoted and bound, key dates, and anything outstanding — alongside the standard policy documents.



**Acceptance Criteria**

**Given **that multiple people at 1 brokerage may be involved in the client journey

**When** the policy is bound and sent to the broker on record

**Then **give** **the person binding the contract the opportunity to enter an alternate email address to which the confirmation of policy details is re-sent.

**Given **that the person binding the policy may not be familiar with the entire journey

**When** the alternative email address field is selected 

**Then **the AI assistant will create a summary which will be part of the cover letter for the email



## Artificial Intelligence (AI)

Brokers are licensed professionals who already understand occupation classes, PI wording and underwriting appetite. The mascot-and-handholding pattern that Frankie presents on Blaze may read as childish in that context, and a more clinical, efficient assistant would earn more trust with brokers.  The current tone of voice (i.e. plain-English BizCover voice — no stiff insurance jargon) should be kept — but there should be a shift in the register from reassuring to precise. Speak to the broker as a peer: state the classification and the reasoning, don’t over-explain terms they already know. Replace exclamation-led prompts with direct, specific ones (e.g. “Occupation matched: Electrician — ANZSIC 3231). Do not use emojis or exclamation marks. 	Replace the illustrated llama avatar with a simple icon or wordmark. Dock the assistant as a workspace panel integrated into the broker’s task. Keep the B4B brand colours for consistency. Brokers must be able to correct a classification instantly — the assistant should not gatekeep their professional judgement. 

Four types of AI touchpoint are used throughout:

- Proactive insight — AI-generated information that surfaces automatically in the workflow (a banner, panel or inline note), generated dynamically from the specific case rather than static per-field text.
- Conversation starter — an entry point (chat icon or prompt box) that lets the adviser ask the assistant something, or that the assistant opens with a question of its own.
- Background instruction — a system-level instruction shaping how the assistant behaves or answers in context; not seen directly by the adviser.
- Canned prompt / action — a fixed, one-click action that triggers a specific AI task without free typing.

Guardrail carried through every item, no AI suggestion in this document is ever auto-applied to the file — the adviser always confirms, and the suggestion plus the adviser's decision is logged.

The AI Assistant will answer questions based on data that has been provided by the business:

- Policy terms and conditions which are available for each product
- Training material supplied by business
- Marketing Material

Below is a summary of areas to be covered by the AI Assistant.  Where relevant further detail has been added to the individual functional requirements describing where the AI Assistant fits in. There is also further detail in the spread sheet on the link <u>https://bizcover.atlassian.net/wiki/x/CoBwHAE</u> as to what is required for the AI Assistant.

  


**Summary of Areas Covered by AI**

| **ID** | **Screen / Functional Area** | **AI Will Assist With** | **Type** |
| --- | --- | --- | --- |
| **AI-00** | Broker Assistant — persona & behaviour | Consolidates the doc's existing AI tone/behaviour paragraph into a usable background instruction. | **Background instruction** |
| **AI-01** | Menu — Start a Quote | Kick off a whole quote from a free-text description, a client website, or an uploaded document. | **Conversation starter** |
| **AI-02** | Occupation Classification | Pre-suggest the best per-insurer occupation match (with confidence + reasoning) instead of the broker checking each insurer's list. | **Proactive insight** |
| **AI-03** | Quick Quote | Give indicative quote for a product not selected | **Conversation starter** |
| **AI-04** | Customer Details | Supplying information around start and expiry dates | **Proactive insight** |
| **AI-05** | Address | On partially entering address lookup must provide address options | **Proactive insight** |
| **AI-06** | Insure Occupations | Explain that multiple occupations may match | **Proactive insight** |
| **AI-07** | Product Eligibility | Explain in one line why a product, insurer or section is unavailable (occupation mapping or dependency rule). | **Proactive insight** |
| **AI-08** | Activity Split | Explain that activities can be searched for | **Proactive insight** |
| **AI-09** | Underwriting | Keep a tally of unanswered questions per product as the broker progresses. | **Proactive insight** |
| **AI-10** | Underwriting | Answer a broker's technical question about a question at adviser-level depth, not customer-tooltip depth. If AI Assistant cannot answer a message is displayed to him asking the broker to contact BizCover. | **Conversation starter** |
| **AI-11** | Interested Parties | Prompt the broker to contact Administrator if Insurable Interest not available | **Conversation Starter** |
| **AI-12** | Get Quote / Selected Quote | Plain-English narrative of the material differences between returned quotes. | **Proactive insight** |
| **AI-13** | Get Quote | Translate a raw insurer decline/error into plain English with a suggested next step. | **Proactive insight** |
| **AI-14** | Premium Adjustment | Draft the audit note for the case file once an Administrator has made an adjustment. | **Canned prompt / action** |
| **AI-15** | Referral to Insurer | Suggest content for insurer-ready referral comments structured to the selected referral reason. | **Conversation starter** |
| **AI-16** | Cross sell | Suggest products for which a quote was not selected but which are available for a specific occupation | **Conversation starter** |
| **AI-17** | Legal Entities | Look up a valid ABN and offer to auto-fill Legal Name / Trading Name or vice versa. | **Canned prompt / action** |
| **AI-18** | Policy Bound | Draft a short handoff note when policy details are sent to an alternate recipient at the brokerage. | **Canned prompt / action** |
| **AI-19** | Search | Notify user that policy in Freeze | **Proactive insight** |
| **AI-20** | Cross-cutting | Guardrail: every AI output above is confirmed by the human and logged — nothing is silently applied. | **Background instruction** |



  


## Help (Tooltips)

As shown in the individual sections above, many of the fields on screens have help functionality (tool tips). The messages on these are somewhat different to those for BlazeX as:  
•	The broker is a different type of persona with advanced insurance knowledge  
•	  The help tool tips must not be in the 2nd person but in the 3rd person (i.e. not “you” but the “the insured”)  
Please find the full list of differences at the link [https://bizcover.atlassian.net/wiki/spaces/BFB/pages/4761485320](https://bizcover.atlassian.net/wiki/spaces/BFB/pages/4761485320) 

## Integration Requirements

| **Interface** | **Description** |
| --- | --- |
| CRM/Salesforce | Customer information |
| Snowflake /Product Engine | Product and pricing data |
| Document Management | Store quotes |
| Email Service | Send quotes |



  


## Integration to Salesforce

**Current Quote Interface from B4B to Salesforce**

When a B4B broker's application is submitted for underwriting and processed by the shared policy engine (MVC), a New Business case is automatically created in Salesforce and tagged to the correct division/queue. This is not a B4B-specific pipe — it is the same general bridge used for all MVC-submitted business — but it is how a broker-originated sale reaches the CRM, and it is live today.

**Quote Interfaces Requirement**

It is anticipated that the same interfaces that have been built for BlazeX/AgentX could be used for BrokerX.

| **Function** | **Description** | **Source Document(s)** |
| --- | --- | --- |
| Create a prospect record in the CRM when a customer starts a quote | As soon as a broker/administrator begins a quote journey and the client’s name is known, BlazeX sends the customer's name through to Salesforce, which creates (or matches to an existing) Account and Contact record tagged as a prospect. This gives sales and marketing visibility of the customer from the very start of the shopping journey. | *blazex-internal.md, blazex-integration.md, blazex-hub-readiness.md* |
| Open a sales case in the CRM to track the quote journey | When a customer's quote journey is under way, BrokerX creates a New Business case in Salesforce linked to the customer and tagged to the BrokerX division, giving the sales/service team a single record to track the prospect's journey from quote through to purchase. | *blazex-internal.md, blazex-integration.md, blazex-hub-readiness.md* |
| Update the sales case with the customer's occupation and industry | Once the customer’s occupation is selected during the quote journey, BrokerX sends the occupation and industry details through to Salesforce, so the sales case reflects what the customer is being quoted for. | *blazex-integration.md, blazex-hub-readiness.md* |
| Record the generated quote(s) against the sales case in the CRM | When BrokerX finishes calculating a quote, it sends the quote details (product, industry, revenue, employee count, location, expiry date, etc.) to Salesforce, which creates an Offer and one or more linked product quote records against the case. This lets sales and reporting teams see exactly what was quoted, something the legacy platform never tracked as separate records. | *blazex-integration.md, blazex-hub-readiness.md, blazex-vs-mvc-gap-analysis.md* |
| Update the sales case when the customer begins checkout | When a customer clicks through to pay for their quote, BlazeX notifies Salesforce, so the case is updated with a payment link and the customer's preferred way of being contacted (email, SMS, or both). – *Need to decide if this step necessary as client does not pay* | *blazex-integration.md, blazex-hub-readiness.md* |
| Share broker information with the CRM for BrokerX quotes | For Broker-X, Salesforce needs to receive broker ID, email, ABN and name so broker-originated business can be tracked and serviced correctly. BlazeX quotes do not currently send any broker details through to the CRM. | *blazex-integration.md, blazex-hub-readiness.md, blazex-vs-mvc-gap-analysis.md* |
| Track marketing promotion and referral source on quotes in the CRM | Like Legacy quotes BrokerX needs to pass promotion codes, affiliate source, and ad-click tracking IDs through to Salesforce so marketing can measure campaign effectiveness. BlazeX does not currently send this information to the CRM. | *blazex-integration.md, blazex-hub-readiness.md, blazex-vs-mvc-gap-analysis.md* |
| Send the CRM's case reference number back to BlazeX | When Salesforce creates a case for a legacy application, it hands the case number back so it can be stored for reference. BrokerX needs the equivalent callback, so BrokerX can store a link to the Salesforce case allowing for staff to cross-reference the two systems. | *blazex-hub-readiness.md, blazex-vs-mvc-gap-analysis.md* |



**Current Bind Interfaces from B4B to Salesforce**

Once a B4B broker's policy is bound, its policy number, dates, premium, insurer and division are sent through to Salesforce and stored as a policy record, so CRM users can see the policy the broker just wrote. As with case creation, this runs through the shared MVC-to-Salesforce bridge rather than anything specific to the broker portal itself, but it does cover broker-written business, and it is live today.

  


**Bind Interfaces Requirements**

It is anticipated that the same interfaces that have been built for BlazeX/AgentX could be used for BrokerX.

| **Function** | **Description** | **Source Document(s)** |
| --- | --- | --- |
| Create the full policy record in the CRM when a policy is purchased | When a BrokerX policy is successfully bound, the full policy is sent to Salesforce: the policy header (premium, dates, insurer, product, insured business details) plus a proper breakdown of coverage sections, individual covers/limits/excess, and the legal entities insured. This will give operations a detailed view in the CRM. | *blazex-integration.md, blazex-hub-readiness.md, blazex-vs-mvc-gap-analysis.md* |
| Attach policy documents to the CRM record at the point of purchase | When a policy binds, BrokerX fetches the signed links to the policy wording, certificate of currency, and tax invoice, and attaches them to the policy record in Salesforce, so customer service staff can open these documents directly from the CRM without needing to log into BrokerX. | *blazex-integration.md, blazex-hub-readiness.md, blazex-vs-mvc-gap-analysis.md* |
| Automatically close the sales case once the policy is purchased | As soon as a BrokerX policy is bound, the related New Business case in Salesforce is automatically closed and marked as won, without any manual step from a salesperson. | *blazex-integration.md, blazex-hub-readiness.md* |
| Clearly identify which policies in the CRM came from BlazeX versus the legacy platform | Every BrokerX policy sent to Salesforce is explicitly tagged with BrokerX-specific reference IDs (policy ID, quote ID, order reference) and a distinct division value, so staff and reports can immediately tell a BrokerX policy apart from a legacy one, rather than having to guess from the record's format. | *blazex-hub-readiness.md, blazex-vs-mvc-gap-analysis.md* |



  


**Integration to Snowflake/Product Engine for Product Data**

*Source of Information is Claude*

| **Function** | **Description** |
| --- | --- |
| BrokerX must read live pricing rules from Snowflake to calculate a quote | The quote-calculation engine is powered with up-to-date rating rules.   Every time BrokerX works out a premium, its Quotations service must read the underlying rating rules — base rates, rating factors, caps and collars, occupation-based eligibility — directly from Snowflake at the moment of quoting, rather than from rules BrokerX's own code. This means when the pricing team changes a rate, BrokerX picks it up automatically without needing a software release |
| Product and pricing changes are loaded into Snowflake for BrokerX to consume | Getting new or updated insurer pricing into the system BrokerX reads from. When an insurer's rates change or a new product is onboarded, BizCover's data team loads the updated rate tables (from an Excel template) into Snowflake, then runs a series of transformation steps that turn that raw data into the clean rating tables. BrokerX reads at quote time. This step is manual today for BlazeX— there's no automated pipeline for it yet. Ideally this project should be used to close this gap. |
| Setting up which questions a product asks and which products a customer is eligible for. | Currently a separate onboarding tool takes the same Excel template used for pricing and generates code changes and database updates that get deployed directly into BlazeX's own database — it doesn't go through Snowflake at all. It's a one-off setup/build step run each time a product is added or changed. This same method could be used to apply data for setting up questions for BrokerX. The preferred route though would be to centralise questions in Snowflake and for them to be pulled into BrokerX. |
| Reporting | The following data needs to be interfaced to Snowflake for BrokerX in the same manner as it is being interfaced for BlazeX: **Policy information** — created the moment a policy is bound: the policy number, which product and insurer it's with, start and expiry dates, which state it's in, the cover sections included, and a breakdown of the premium. It also carries a reference back to the customer and to the quote it came from. Customer (contact) details — name, email, and phone number. Interestingly this comes from a different part of BlazeX than the policy itself (the customer-facing "Hub" side, not the policy engine), so it's tracked as its own separate piece. Quote/pricing detail — every time a quote is generated, the full price breakdown goes across: total premium, base premium, stamp duty, underwriting fee, platform fee, and the GST on each of those. Commission — how much commission is earned on the sale, and the GST on it. The insurer's share — how much of the premium is owed to the underlying insurer, and the GST on that portion. Payment/receipt information — what the customer actually paid, when, how (*will always be from Broker’s commission account*), and any. Transaction type and channel — whether it's new business, an endorsement/amendment, or a renewal, and which sales channel it came through. Broker attribution — for broker-sold business, which brokerage the sale belongs to, which is what feeds broker performance numbers. Website/marketing activity — BlazeX's website analytics (Google Analytics event tracking) is also being connected into Snowflake, as a newer addition mainly for marketing use. |



  


**Integration between BrokerX and Tools portal**

*Source of Information is Claude*

| **Function** | **Description** |
| --- | --- |
| Broker Maintenance | Broker Maintenance is a Tools Portal screen used to create, search and edit broker and brokerage records (Information such as whether the broker is active, if his account is locked or account sharing or commission percentage) — it is an administrative data-entry function, not a broker self-service tool. The information loaded would be common to both B4B and BrokerX therefore at current point Broker Maintenance will remain on Tools portal and will be consumed by B4B and BrokerX. The data entered on Broker Maintenance also drives Monthly Broker Statements and Broker Payment Reconciliation. While the brokers account details (name, address and phone number) can be changed on Tools Portal there is currently functionality on B4B to do this and this same functionality will be available on BrokerX. BrokerX will therefore need to store changes to the Broker Details table used by Tools portal. |
| Adding & Maintaining Endorsements | At current point the creation and maintenance of Endorsements will continue to be done on Tools Portal with the storing of data on MVC. As for BlazeX, for BrokerX endorsement data will be retrieved from MVC for selection on BrokerX. |
| Embargos | Postal codes for which embargos are in place are stored on Tools Portal. These records will need to be available to the BrokerX database so that when New Business quoting occurs the relevant postal codes will be flagged. |
| Endorsement Override | To be discussed |

  


## Integration to Document Management

|   |   |   |
| --- | --- | --- |
| **Quote** -Printable quote summary produced during the quote journey | While a broker is still shopping for a quote (before the policy is bought), they can request a quote schedule document summarising the current quote. BrokerX's Documents module must generate this on demand from the live quote data. | Quote Schedule |
| **Bind **- Core policy pack issued when a customer buys a policy | When BrokerX successfully binds a new policy, it must trigger the Document Generation service to produce the customer's core policy pack. The finished PDFs must be stored in Amazon S3 and linked to the policy record. This process has already been done for BlazeX and thus should be able to be copied except for CoC which may not yet have been done. | Policy Wording,    Product Disclosure Statement (PDS),   Certificate of Currency (CoC) |
| **Bind** -Supporting paperwork issued alongside the policy pack | Beyond the core pack, BrokerX's Documents module must also be able to produce a cover letter, a policy schedule and a signed declaration for the new policy, each available as a document or a direct link. | Cover Letter, Policy Schedule, Declaration |
| **Ongoing - **Staff, brokers or customers retrieving a policy's documents after the fact | Every document generated for a policy is stored in Amazon S3. BlazeX Hub lets an authenticated caller list every document held for a policy and download a specific one via a secure, time-limited link, rather than exposing the file store directly. | Any previously generated document (Policy Wording, CoC, PDS, Schedule, etc.) |
| **Wording** | On documents generated for journeys completed via BrokerX instead of an Application ID the Transaction Ref (Journey Code) must be displayed. | Welcome, Declaration, Invoice |

  


## Welcome Letter

*[embedded media/image omitted]*

  


## Declaration

*[embedded media/image omitted]*

## Invoice

*[embedded media/image omitted]*

## Integration to Email 

Currently from B4B brokers can email various documents to their clients. These include:  
•	Quotes  
•	Certificate of Currency  
•	Declarations  
•	Invoices  
•	Payment Schedule  
•	Policy Schedule  
•	Terms  
•	Endorsements  
The understanding is that BlazeX has not been built with the capability to integrate directly to email services but that the emails are sent from a link in Salesforce. This will need to be different for brokers as they will make the request for an email from BrokerX. For informational purposes in the current B4B platform the functionality works as per below:  
•	Quote emailed to a broker — handled by BCQuoteEmailService. When a quote is saved and sent (SaveQuoteAndEmail()), it emails the broker with attached PDFs: the quote comparison, terms, and a Q&A summary. When a broker specifically sends a quote to their client (via the broker portal's "Send to Client" action), the same underlying dispatch (Application.SendToClient) fires with the same attachments.  
•	Policy pack emailed after a purchase (bind) — handled by BCDocumentGenerationService. Once a policy is bound, the full document bundle must be generated (policy wording, Certificate of Currency, terms, payment schedule, any endorsements, credit note if relevant). Everything must be merged t into one PDF, uploaded to S3, and then sent as a confirmation email with that bundle attached — unless email has been explicitly suppressed for that transaction. These documents also need to be able to be emailed separately on request. 

## **Security Requirements**

| **Requirement ID** | **Requirement** |
| --- | --- |
| SEC-001 | Users must authenticate via SSO. |
| SEC-002 | Role-based access control enforced. |
| SEC-003 | Actions audited. |
| SEC-004 | Pricing changes logged. |
| SEC-005 | Destroying or deidentifying data |

## SEC-01 —Authentication

  
**Detail**  
•Brokers must be able to sign in using a username and password.  
•At current time this should match the sign on he has for B4B as he will need to work concurrently on B4B and BrokerX for approximately a year.    
•Multi Factor (MFA) authentication would be preferred for this system

##    
SEC-02 —Role Based Access Control

**Detail**  
•A proper set of named roles and 54 individual permissions (things like who can cancel a policy, who can override a price, who can move dates around) that apply to a person.  
•Automatic scoping of a broker to only their own clients (unless it's deliberately shared with their brokerage).  
•A specific permission that controls who is allowed to manually override a calculated price.  
•Super-Agent Admin elevated permission users should be able to override the data on the policy (endorsements, premiums, document template, coverage components, etc). This should record what the original value was and what the new values are for auditing

##   
SEC-03 —Actions Audited

  
**Detail**  
•A record of every time an admin or broker signs in, with a timestamp.  
•Ensure all transactions record which platform was used for regulatory audit, dispute resolution, and compliance purposes  
•A full audit trail of policy actions (bind, amend, cancel, renew and referral) is required.  
•Active alerts to items appearing on security logs and real time monitoring of these logs. BizCover needs to be able to notice breeches quickly enough to assess it and report on it to the OAIC (Office of the Australian Information Commissioner).  


## SEC-04 —Pricing Changes Logged

  
**Detail**  
Premium changes must be published as a PolicyPremiumBearingAmendedEvent carrying old and new premium and effective date, and the current premium breakdown. Currently on AgentX no dedicated change-audit log was found for edits to the underlying rating/fee configuration tables. Confirmation is required if this will be necessary for BrokerX.

##   
SEC-05 —Destroying and De-Identifying Data

  
Detail  
BrokerX will need a specific retention policy (i.e. how long we keep data after the client has cancelled his policy or his policy has expired). It is assumed this will be 10 years as this is the retention requirement for BlazeX.  
Note: If all of the above security measures are not in place BizCover breech the Privacy Act 1988 and its "Australian Privacy Principle 11" (APP 11), which says a business must take "reasonable steps" to protect personal information — and the regulator's own guidance spells out what that generally includes: access controls with logs and audit trails, and destroying or de-identifying data once it's no longer needed

## Reporting Requirements/Analytics

While analytics are outside the BrokerX system, the BrokerX system needs to be able to pass sufficient information that the following insights are available:

- Product and Quote submission rates
- Sales Insights
- Sales Revenue
- Sales per Brokerage
- Sales per Broker

## Performance

- Quote retrieval < 2 seconds.
- PDF generation < 10 seconds.



## Availability

- 99.9% uptime.



## Uniformity

- Since our offering will be across the B4B and the new BrokerX platform for the cut over period, we need to insure the following:
- Ensure identical product, pricing, terms, Product Disclosure Statement, and Target Market Determination across both platforms to maintain regulatory compliance and consumer protection
- Verify commission rates and structures are identical across platforms to prevent unfair consumer outcomes.
- Ensure all transactions record which platform was used for regulatory audit, dispute resolution, and compliance purposes
- Ensure that current Tools portal capabilities are available to users when using Broker-X

  


# Glossary



| **Term** | **Name** | **Description** |   |
| --- | --- | --- | --- |
| **AI** | Artificial Intelligence | Artificial Intelligence (AI) is the simulation of human intelligence by machines, enabling them to learn, reason, and make decisions. |   |
| **ABN** | Australian Business Number | An ABN (Australian Business Number) is a unique 11-digit identifier issued by the Australian Government that businesses use for tax, invoicing, and dealings with government agencies. |   |
| **AXP** | AgentX Portal | The Tools Portal application for internal agents |   |
| **BlazeX** | BlazeX Platform | Core insurance policy management system |   |
| **BrokerX** | BrokerX Platform | New core insurance policy management system for brokers and administrators. |   |
| **B4B** | Broker Portal | Legacy Policy Management Platform for Brokers and Broker Administrators |   |
| **ESL** | Emergency Services Levy | Government-mandated insurance levy |   |
| **GST** | Goods and Services Tax | Australian consumption tax (10%) |   |
| **ID** | Identifier | Unique reference number |   |
| **Journey ID** | Journey ID | A unique (GUID) identifier for one journey session, used to link that session's data and actions across the front-end app, caching layer, logging, and downstream systems like Salesforce. |   |
| **LMI** | Labour Market Information | Classification code for business occupations |   |
| **MVC** | Model-View-Controller | Legacy platform being replaced |   |
| **MFA** | Muti Factor Authentication | t is a security control that requires a user to provide two or more forms of verification before gaining access to a system. The Three Common Authentication Factors: - Password - PIN - Security question |

| **OAIC** | Office of the Australian Information Commissioner | OAIC stands for the Office of the Australian Information Commissioner. The OAIC is Australia's independent regulator responsible for: Privacy regulation under the Privacy Act 1988 Freedom of Information (FOI) oversight Management of government information policy For insurers and insurance brokers, the OAIC is the primary regulator overseeing how personal information is collected, used, stored, disclosed, and protected. The OAIC also investigates eligible data breaches and privacy complaints. |
| --- | --- | --- |
| **PDS** | Product Disclosure Statement | Legally required document an insurer gives a customer before they buy a policy, explaining what's covered, what's excluded, the cost, the excess, and how to make a claim. |   |
| **RBAC** | Role-Based Access Control | Permission management system |   |
| **TMD** | Target Market Determination | Who a product is designed for and who it isn't — the kind of customer, their likely needs, and circumstances where the product would be a poor fit. |   |
| **UI** | User Interface | Visual screens and elements |   |



  


# Sources

| # Process | # Sources |
| --- | --- |
| New Business Functional Document | AgentX Phase2 New Business Functional Document https://bizcover.atlassian.net/wiki/x/BABc9 |
| APIs | AgentX New Business API Spec https://bizcover.atlassian.net/wiki/spaces/BFT/pages/4124213249/AgentX+New+Business+-+API+Spec |
| Artificial Intelligence | BA Toolkit → repos/BizCover.Web.BlazeX.CustomerPortal: README.md, DESIGN.md, app/lib/ai/** (tools/, frankie/, mcp/, providers/, voice/, vector-store/, system-prompt.ts, config.ts), src/mastra/** BA Toolkit → repos/BizCover.MCP.OpenAI.Bizify: README.md, server/mcp/** (server.ts, indicativeService.ts, occupationService.ts, journeyService.ts, config.ts, aiService.ts), docs/SUBMISSION.md, docs/PRIVACY.md, docs/DO-3938-ipg-auth-migration.md BA Toolkit → docs/codex/repos/BizCover.Quotations: README.md, api.md (confirms the Quotations module — “Blaze Modular Monolith for Quotations” — as the owner of the indicative-offer endpoint Bizify calls) BA Toolkit → docs/codex/business-flows/bizcover-ingests-new-knowledge-into-the-ai-assistant.json (background on BizCover's separate staff-facing knowledge-base assistant, which Frankie also draws on via the shared MCP knowledge-base retriever) BA Toolkit → docs/integrations/blazex-internal.md, docs/projects/AI, BZAI and OZAI team.md (organisational context for BizCover's AI initiatives) |
| Salesforce Integration | BA Toolkit → docs/integrations: salesforce-bridge.md, blazex-internal.md BA Toolkit → docs/platforms/salesforce: README.md, api-bridge.md, blazex-integration.md, blazex-hub-readiness.md, blazex-vs-mvc-gap-analysis.md, case-management.md, claims.md, communications.md, failed-payments.md, integrations.md, mvc-integration.md, renewals.md, self-service.md, diagrams/amendment-consumer-sequence.ascii, diagrams/blazex-quote-to-bind-sf-sequence.ascii BA Toolkit → docs/platforms/blazex: README.md, hub/README.md, policies/README.md, quotations/README.md BA Toolkit → docs/codex/repos: BizCover.Api.SalesForce (api.md, config.md, README.md), BizCover.BlazeX.Hub (api.md, domain.md, README.md) BA Toolkit → docs/migration/gap-analysis.md, docs/features/integrations/README.md BA Toolkit → Cancellation_Referral_Products_and_Triggers.docx |

| Documentation Integration | BA Toolkit → docs/integrations/blazex-internal.md, docs/migration/gap-analysis.md BA Toolkit → docs/platforms/blazex/hub/README.md, docs/platforms/blazex/policies/README.md BA Toolkit → docs/repos/bizcover-blazex-hub/README.md, docs/repos/bizcover-policies/README.md, docs/repos/bizcover-quotations/README.md BA Toolkit → docs/repos/bizcover-integration-service-documentgeneration/README.md BA Toolkit → docs/codex/repos/BizCover.Web.DocumentAdminApp/README.md, docs/repos/bizcover-web-documentadminapp/README.md BA Toolkit → docs/features/document-management/README.md (legacy MVC — reviewed for comparison context only), docs/features/integrations/README.md |
| --- | --- |

