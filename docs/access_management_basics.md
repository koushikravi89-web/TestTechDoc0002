## Determining Access Permissions

In line with XELERATE's mission to enhance transparency and accessibility across CARIAD's software ecosystem, it's crucial to maintain compliance and security standards. This is important as XELERATE uses Cloud IDP for authentication, allowing anyone authenticated via Cloud IDP to view discoverable developer assets. This includes all persons worldwide with a KUMS ID in the VW Group and all partners as well as vendors alike.

We adhere to a "need-to-protect" ethos, consistent with other knowledge sharing platforms at CARIAD like Confluence. This approach emphasizes opening access wherever feasible and reserving protections for assets that truly necessitate safeguarding due to compliance considerations (outlined below).

This guide is designed to help content publishers on XELERATE determine who should have **full, limited or denied access** to their API specifications, documentation, and other developer assets. The following dimensions address key compliance considerations to ensure access is granted appropriately to specific users, teams, companies, or regions.

### Confidentiality
Confidentiality ensures that sensitive information is protected from unauthorized access or disclosure. As you determine access, consider the following:

1.	**Identify Confidential Information**: Determine which parts of your content are considered confidential and require restricted access. Foster a culture of protecting information rather than strictly limiting access. Allow default access unless necessary to restrict.
2.	**Non-Disclosure Agreements (NDAs)**: Anyone with read access to confidential information may need to sign an NDA to ensure confidentiality. Note that NDAs with contractors at CARIAD solely apply to the local project context.
3.	**Secret Information**: Do not publish any information that is classified as “Secret”. 

> **Note**: While the need-to-protect principle allows for sharing most of the content within CARIAD SE, this may not apply to all partners, vendors and markets. Please adjust your access settings accordingly. For detailed guidance on how to apply such restrictions continue reading.

**Contacts for Confidentiality Support**

- SE-C: Corporate Security & Environment
- [Introduction to Information Classification](https://volkswagen-net.de/wikis/display/Informationsklassifikation/Introduction+to+the+subject+of+information+classification)

### Export Control
Export control regulations are rules set by governments to prevent the export of goods, technology, and information that could threaten national security, foreign policy, or economic interests. These rules aim to stop sensitive information and technology from reaching unauthorized individuals or groups who might misuse them.

**Why Export Control Matters**

Following export control regulations is crucial for companies because it:

- Protects sensitive information from being disclosed to unauthorized parties.
- Ensures that the company adheres to legal requirements, avoiding penalties.
- Helps maintain national and international security.

**Applying Export Control in the Developer Portal**

When setting access permissions for your assets in the developer portal, consider the following steps to comply with export control regulations:

1.	Do you plan to involve EU or US restricted parties in your project? (e.g. Huawei)
2.	Are you working with listed hardware under certain Classification numbers (e.g. 6A003 Infrared cameras)? Associated software and technologies also need to comply with export control!
You can find those ECCN and HTS numbers on the manufacturer's website, an overview of restricted numbers relevant for CARIAD will be provided here: [Export Control at CARIAD](https://volkswagen-net.de/wikis/display/Cariad/Export+Control)
3.	Do you work with partners e.g. "Apple Pay" or "Amazon Alexa"?  Their requirements may result in export control restrictions!
4.	Do you use cryptography that is not 100% open-source?
5.	Do you work with technology/knowledge with connections to aerospace, intelligence or the military sector? 

If one of the above questions is answered with yes, you should schedule a meeting with the export control support.

**Important Notice for Users from outside of Europe**

XELERATE is a developer portal hosted in Europe. When publishing your assets, please be aware that this constitutes an export of digital assets to Europe, which may be subject to export control regulations. This applies especially for teams from China and USA.

**Contacts & Resources for Export Control**

- FA-B: Treasury, Tax & Export Control [(&#9993; Contact: Sirid Alina Lühr)](mailto:SIRID.ALINA.LUEHR@CARIAD.TECHNOLOGY)
- [Export Control Support for Tech Centers](https://devstack.vwgroup.com/confluence/display/LEGALDP/06_Export+Control+T-Department)
- [Export Control of software & technology](https://volkswagen-net.de/wikis/pages/viewpage.action?pageId=3429467187)

### eDiscovery

eDiscovery refers to identifying, collecting, and producing electronic information for legal or regulatory purposes. It's crucial for compliance when deciding who should have access to specific content.

1.	**Data Preservation**: Ensure that information potentially subject to eDiscovery is preserved and cannot be altered or deleted. This impacts who should have read access to this data.
2.	**Data Collection**: If read access involves extracting data, ensure it's done securely and in a way that maintains data integrity.
3.	**Compliance with Laws**: eDiscovery requirements vary by jurisdiction. Consider these when deciding who should have access to ensure compliance with privacy and data protection laws.

**Contacts & Resources for eDiscovery**

- GL: Legal [(&#9993; Contact: Tobias Kugler)](mailto:tobias.kugler@cariad.technology)
- [Basics of eDiscovery](https://volkswagen-net.de/wikis/pages/viewpage.action?pageId=2941879875)
