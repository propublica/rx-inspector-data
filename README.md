# Rx Inspector Public Data Release

![Pill illustration by Sophi Miyoko Gullbrants for ProPublica. Code screenshot by ProPublica. ](https://www.propublica.org/wp-content/uploads/2026/01/20260121-fda-inspector-code.jpg?w=1149)

ProPublica is publishing never-before-released data connecting generic drugs to the factories that manufactured them. The data powers [Rx Inspector](https://projects.propublica.org/rx-inspector/), our groundbreaking tool that allows you to find the factories where your generic drugs were made and their Food and Drug Administration inspection track records.

The data, which ProPublica created by linking several FDA datasets, has never been made available by the agency before. It will allow anyone to connect prescriptions to the facilities they were manufactured in by linking National Drug Code numbers to FDA Establishment Identifiers of drug manufacturing facilities. You can download the [FDA National Drug Code directory](https://www.fda.gov/drugs/drug-approvals-and-databases/national-drug-code-directory), which has drug name and dosage information, and the [FDA list of currently registered facilities](https://www.fda.gov/drugs/drug-approvals-and-databases/drug-establishments-current-registration-site), which has addresses and company names.

This data was last updated in November 2025.

If you are a journalist or researcher, we’d be interested to know how this database helps you do your work. Please email us at [FDA@propublica.org](mailto:FDA@propublica.org) to get in touch.

## Data Dictionary

### **ndc**

National Drug Code (NDC) number for this drug, as found in the [Structured Product Labeling (SPL) database](https://dailymed.nlm.nih.gov/dailymed/spl-resources.cfm). Full NDCs are made of three segments, separated by dashes. The segments describe the labeler (company name, not to be confused with the manufacturer), product (e.g., drug and dosage) and package (e.g., number of pills in a bottle). The NDCs in this column are product NDCs, meaning they will have only the first two segments. You can safely search for a three-segment NDC in this data by using only the first two segments. [You can read this FDA document](https://www.fda.gov/media/173715/download) describing what NDCs are, the different NDC formats and how to convert between them.

### **fei**

[FDA Establishment Identifier](https://www.accessdata.fda.gov/scripts/cdrh/cfdocs/cfRL/rl.cfm) (FEI) for a facility we connected to this drug.

### **registrant\_name**

The name of the company that registered the facility with the FDA. This is sometimes the same as the labeler of the drug, but not always.

### **country**

The [ISO 3166-1 alpha-2 code](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) of the country (e.g., US, IN) where the facility is located. This is determined from the registered address.

### **api\_mfr**

This is set to TRUE if the labeler indicated this facility was a maker of only the raw active ingredients, or an active pharmaceutical ingredient (API), of the drug product.

### **linkage\_method**

This field denotes the method ProPublica used to connect this drug to a facility in the FDA’s current or historical listing of drug manufacturers. It has two possible values:

`SPL_DUNS_FEI` — The drug’s label contains an FEI or Dun & Bradstreet (DUNS) identifier that we used to look up a facility.

`ADDRESS_MATCH` — This means we performed address matching to link the drug to a facility. The address came from one of two sources:

1. ProPublica was able to find the product’s abbreviated new drug application (ANDA) number and look up a facility address in a spreadsheet of generic drug manufacturing locations that ProPublica obtained after suing the FDA for the records.

2. The facility address was printed in the text of the drug label (e.g., “Manufactured by: Company Labs Inc, 100 Main St, NY”), and ProPublica matched it to an FDA facility using fuzzy text matching and geocoding.

### **anda**

An ANDA is a code uniquely identifying an FDA approval of a generic drug product. We include it here if one was in the SPL record.

### **bla**

A Biologics License Application (BLA), which identifies approval to manufacture a generic biologic product.

### **nda**

A New Drug Application (NDA) number, identifying a brand-name drug approval. Rx Inspector provides information only on generic prescription drugs, excluding brand names, with the exception of authorized generics. These are [defined by the FDA](https://www.fda.gov/drugs/abbreviated-new-drug-application-anda/fda-list-authorized-generic-drugs) as an “approved brand name drug that is marketed without the brand name on its label.” A record with an NDA listed indicates this drug is an authorized generic.

## About this Data

#### **What Is Rx Inspector?**

Labels on pill bottles may list the distributor or repackager of a generic drug, but they don’t always show where it was really made. Without that critical information, you can’t learn what the Food and Drug Administration discovered if and when that factory was inspected for quality and safety violations.

[Now you can.](https://projects.propublica.org/rx-inspector/)

To bring more sunlight to the world of drug manufacturing, ProPublica connected the disparate databases and websites where the FDA scatters this information. We also obtained documents stemming from thousands of FDA inspections of generic drug factories since 2008. At one point, we sued the FDA in federal court for factory locations and received a partial list.

Our database will show you the facility that manufactured your prescription generic drugs and any inspection reports we have from the FDA.

The data is not perfect: It is possible the FDA’s information is not up-to-date because, for example, one company acquired another or moved its manufacturing to a different location. However, we believe this is an important first step in shedding light on a process that the agency and drugmakers have sought to keep secret from consumers.

#### **Which Drugs Are Included?**

Our ongoing reporting has focused on the safety of generic drugs, which represent the vast majority of all prescriptions filled in the United States. Thus, the tool does not include brand-name or over-the-counter drugs. Further, we excluded gases (like oxygen tanks) and intradermal route drugs (many of these were allergy tests for things like feline hair). We included biological drug products, such as insulin. We opted to include [authorized generics](https://www.fda.gov/drugs/abbreviated-new-drug-application-anda/fda-list-authorized-generic-drugs), which are brand-name drugs that are marketed without the brand-name label, because we thought consumers may not know their “generic” is actually a brand-name drug.

#### **How Did ProPublica Connect This Information?**

We have written [an in-depth methodology](https://www.propublica.org/article/rx-inspector-fda-generic-drug-tool-methodology), but in short, we connected several FDA databases to make Rx Inspector:

* The Structured Product Labeling database.
* The National Drug Code Directory.
* The Electronic Drug Registration and Listing System.
* Data from the agency’s inspection dashboard.
* A spreadsheet of facility addresses we sued the FDA for, which connected them to drug application numbers.
* Form 483 documents we received from a Freedom of Information Act request.

ProPublica described the app and the methodology used to build it to the FDA, which did not comment. The agency previously told ProPublica that it doesn’t reveal where drugs are made on inspection reports to protect what it deemed confidential commercial information.

#### **What Can I Do With This?**

This data enables aggregate analysis and summaries that aren’t possible using Rx Inspector alone. For example, using the linkage categories included in the spreadsheet, pharmaceutical researchers can quickly see what percentage of generic drugmakers provided the manufacturing locations and their IDs on their labels.

They can also compare drugmakers across countries and within drug classes by pulling in other data sources containing FDA Establishment Identifiers and National Drug Codes. Cross-referencing the FDA’s public inspections dashboard will allow analysis like how often the FDA conducts routine manufacturing inspections on facilities by country.

#### **How Do I Report Incorrect Information?**

If you work for a manufacturer or otherwise see that information we are displaying may be incorrect, please email [FDA@propublica.org](mailto:FDA@propublica.org).

## Licensing

We are releasing this data under [a Creative Commons BY-NC 4.0 license](https://creativecommons.org/licenses/by-nc/4.0/), meaning you may use it for noncommercial purposes as long as you attribute ProPublica and link back to [Rx Inspector](https://projects.propublica.org/rx-inspector/).


