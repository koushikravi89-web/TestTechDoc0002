## How to Specify Access to Your Assets

To manage who has access to your content, you have various options at your disposal. We use three different access groups to control permissions:

**1.	Full access:** Users and/or groups that are listed here, will have full read access to your content (incl. API specifications and tech docs)

**2.	Limited access:** Users and/or groups that are listed here, will be able to discover your assets in the software catalogue. However, these users will only view the “Overview Page” for your entities while API specifications and tech docs will be hidden. As the overview page also contains information about the owners of the entity, users will be able to contact them directly and request access if needed.

<img src="../img/overview.png" alt="Overview Page" style="box-shadow: 3px 3px 3px gray;">

> This is the overview page that will be visible to users with limited access. All other menu tabs (e.g. Docs, API) will be restricted.

**3.	Blocked access:** Users and/or groups that are listed here, will not be able to discover your entities in the software catalog. This is the most restrictive setting that you can choose regarding visibility of your content. 

> Note: The settings you choose for these three groups will always apply to the whole repository the catalog-info.yaml is attributed to. 

### How To Maintain the Access Groups 

In XELERATE we offer multiple values to be chosen for settings restrictions:

**1.	Restricting Access to Individual Users:** To allow specific users access, add their email addresses to either the “full-access”, “limited-access” or “blocked-access” attribute within the catalog-info.yaml file.
```sh
full-access = [name.surname@example.com, john.doe@cariad.technology]
limited-access = [name.surname@cariad.us]
blocked-access = []
```

**2.	Limiting Access to Groups:** You can limit access to certain “Groups” within XELERATE. Groups are automatically created when content is onboarded by a group. 
To add a group just list the name of the group in either the “full-access”, “limited-access” or “blocked-access” attribute within the catalog-info.yaml file.

```sh
full-access = [my-team]
limited-access = [team-xy]
blocked-access = []
```

> To find out which groups are available, check [here](https://developer.cariad.digital/catalog?filters%5Bkind%5D=group&filters%5Buser%5D=all). For more information on how groups work, read this: [Link to documentation]

**3.	Restricting Access to Specific Companies:** If you want to grant access to users from specific internal companies (e.g. CARIAD SE), add the respective Company Codes to one of the available attributes. 

```sh
full-access = [007152, 000100] #Company Codes for CARIAD SE & Volkswagen AG
limited-access = [006840] #Company Code for CARIAD China
blocked-access = []
```

> You can find the list of available company codes here: [LEMI – Legal Entity Management Information](https://group-wiki.wob.vw.vwg/wikis/display/GroupLegal/LEMI) (only accessible for internal employees).

Here is an example list of the most common company codes:

| companyCode | Company Name |
| ------ | ------ |
| 007152 | CARIAD SE |
| 000100 | Volkswagen AG |
| 000200 | Audi AG |
| 00H001 | Porsche AG |
| 004042 | CARIAD Inc. |
| 006840 | CARIAD China |
| 007153 | CARIAD Estonia |

**4.	Limiting Access to Regions:** To restrict access by region, use the following codes:

- "NAR" for North America (Canada & USA)
- "CHN" for China

```sh
full-access = [NAR]
limited-access = [CHN] 
blocked-access = []
```

These regions are based on the legal affiliation of the companies in each group. E.g. all companies with a legal affiliation in China are assigned to the region CHN. The specific legal affiliation per country can be looked up here: [LEMI – Legal Entity Management Information](https://group-wiki.wob.vw.vwg/wikis/display/GroupLegal/LEMI) (only accessible for internal employees).

**5.	Restricting Access to Internal or Contractor Users:** If you need to limit access to employees within the VW Group or contractors, use "internal" or "contractor." Internal users are VW Group employees (including subsidiaries), while contractors are direct suppliers or external workers affiliated with VW Group companies or subsidiaries.

```sh
full-access = [internal]
limited-access = [contractor] 
blocked-access = []
```

> Note: The group “internal” does not contain employees from China and North America. If you want to use these specifically, please refer to region-based access control mentioned above.

### Order of Processing & Exception Handling
The different access groups are prioritized such that higher graded permissions take precedence over lower graded ones. For example, if a user is included in both “limited-access” and “full-access” groups, the system will grant full access rights.

This mechanism helps streamline access management for large user groups.

**Examples**

If you want all internal users to have limited access to your content but want CARIAD SE employees to have full access, you can add “CARIAD SE” to the “full-access” group and “internal” to the “limited-access” group. Even though CARIAD is part of the “internal” group, it will receive additional permissions as it is in the higher graded access group.

```sh
full-access = [007152] #CARIAD SE company code
limited-access = [internal] 
blocked-access = []
```

**Fallback Behavior**

In case a user cannot be assigned to one of the groups the system will internally assign users to the field “limited-access”.  
So, a setting like in the example below, would lead to users from a contractor being treated as if they would have been added to the "limited-access" list:

```sh
full-access = [internal] 
limited-access = [CHN, NAR] 
blocked-access = []
```

This logic aims to ensure that transparency and accessability is maximized. If this is not wished it can be easily changed by the controls described above.

When using the catalog-info.yaml template that is provided by XELERATE these will be the soft default values that will apply to most teams.
```sh
full-access = [007152] #CARIAD SE company code
limited-access = [internal, contractor, CHN, NAR] 
blocked-access = []
```
Adjust this as needed by your project.
