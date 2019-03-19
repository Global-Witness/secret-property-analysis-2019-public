## Anonymously owned property analysis 2019

==========================

This analysis quantifies the amount of property in England and Wales owned by companies incorporated in secrecy jurisdictions.

This analysis uses Land Registry data accurate as of 1st January 2019. The dataset used is the [Overseas Companies Ownership dataset](https://www.gov.uk/guidance/hm-land-registry-overseas-companies-ownership-data), it is available free of charge from the Land Registry. It contains information on leaseholds and freeholds in England and Wales owned by non UK registered companies. A country is considered to be a secrecy jurisdiction if it has a secrecy score 60 or above in the [Tax Justice Network Financial Secrecy Index](https://www.financialsecrecyindex.com/). A list of the British crown dependencies and overseas territories can be found [here](https://en.wikipedia.org/wiki/Crown_dependencies) and [here](https://en.wikipedia.org/wiki/British_Overseas_Territories).

## Press

This analysis was written up in [The Observer on 19th March 2019](https://www.theguardian.com/uk-news/2019/mar/17/100-billion-of-uk-propert-secretly-owned-anonymous-firms-tax-havens). It also appears in a Global Witness blog post [here](https://www.globalwitness.org/en-gb/blog/brexit-chaos-should-not-distract-from-cleaning-up-britains-property-sector/).

## Primary data sources

- [England & Wales Overseas Companies Ownership dataset](https://www.gov.uk/guidance/hm-land-registry-overseas-companies-ownership-data)
- [Tax Justice Network Financial Secrecy Index](https://www.financialsecrecyindex.com/)

## Data analysis

All the data analysis summaries and steps can be found in [`notebooks/overseas_ownership_analysis_2019.ipynb`](https://github.com/Global-Witness/secret-property-analysis-2019/blob/master/notebooks/overseas_ownership_analysis_2019.ipynb).

## Data processing steps

Data processing steps are performed in the first cell of [`notebooks/overseas_ownership_analysis_2019.ipynb`](https://github.com/Global-Witness/secret-property-analysis-2019/blob/master/notebooks/overseas_ownership_analysis_2019.ipynb).

- Transform the original Land Registry data so that there is one property owner per line. This means that one title may appear across a number of rows, therefore additional steps are needed to de-duplicate this data when performing counts in the analysis
- Clean the country fields and perform some other basic cleaning operations
- Add additional fields to help with analysis e.g. company incorporated in secrecy jurisdiction (see more in Data Dictionary)

## Get in touch

Get in touch with Sam Leon (sleon@globalwitness.org) if you have any questions about this analysis.

## License

This work is published under the [Creative Commons ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/legalcode).

## Data dictionaries

Where fields occur in original Land Registry dataset, descriptions are taken from [gov.uk documentation](https://www.gov.uk/government/publications/overseas-companies-chargeable-dataset-data-specification/overseas-companies-chargeable-dataset-data-specification#data-content-and-structure).

Below are the definitions for the fields of the table used in the analysis found in [`notebooks/overseas_ownership_analysis_2019.ipynb`](https://github.com/Global-Witness/secret-property-analysis-2019/blob/master/notebooks/overseas_ownership_analysis_2019.ipynb). This table has been exported as `data/processed/full_stacked_cleaned_data.csv`

Column name | Data type | Description
--- | --- | ---
Title_Number | String | Number which uniquely identifies a registered title to land or a caution against first registration.
Tenure | String | Freehold or Leasehold.
Property_Address | String | The unformatted A1 Address entry or an address from the Land Registry Property Gazetteer (LRPG)
Price_Paid | Float | The sale price stated on the transfer deed. Highly incomplete, see below. Prices not included for properties part of a larger deal.
District | String | 	District name. Name of an administrative district created since local government reorganisation 1974. Administrative district also covers the London boroughs, unitary authorities and (for HM Land Registry’s purposes) the Isles Of Scilly parishes.
County | String | County. Name of current County in England and Wales.
Region | String | 	Region name. Name of a geographic region which comprises one or more current counties, former counties or unitary authorities or any combination of these. On HQ instructions, the names and extents of the regions are the economic planning regions used by various bodies. N.B. region names allocated by the Office for National Statistics differ in some instances from names in this field.
Postcode | String | Postcode. Code which is a combination of up to 7 letters and numbers (plus one embedded blank), which defines different levels of geographic units. It is part of a coding system created and used by the post office across the UK, to facilitate the mail service.
Date_Proprietor_Added | Date | The date a proprietor was added to the register.
Additional_Proprietor_Indicator | Boolean string (Y/N) | Indicator as to whether there is more than one proprietor for the property.
Multiple_Address_Indicator | | Indicates the title has more than one address.
Proprietor_Number | Integer | Ordinal number representing the number of the proprietor in event that there are multiple
Company_Registration | String | Company Registration Number. Number which is a unique identifier assigned to a company when it is registered at Companies’ House. Although the name of the company may change, the company registration number will remain the same.
Country_Incorporated | String | The name of the country where the company/territory is incorporated.
Proprietor_Address_1 | String | Register address string. Text which is the address (including the postcode) either of a property or a registered proprietor, in the form in which it appears as the property description on the register. 
Proprietor_Address_2 | String | Register address string. Text which is the address (including the postcode) either of a property or a registered proprietor, in the form in which it appears as the property description on the register.
Proprietor_Address_3 | String | Register address string. Text which is the address (including the postcode) either of a property or a registered proprietor, in the form in which it appears as the property description on the register.
Proprietor_Name | String | Non – Private Individual Name. Name of a company, corporate body, local authority or other organisation or establishment other than that of a private individual.
Proprietorship | String | Name category description. Text which describes the category in which a name falls.
incorporated_normalized | String | Cleaned version of Country_Incorporated to allow for easier analysis. Not in original data.
secrecy_jurisdiction | Boolean | True if country of incorporation is in a secrecy jurisdiction. Secrecy jurisdictions are countries or territories which have secrecy score of 60 or above in [Tax Justice Network's 2018 Financial Secrecy Index](http://www.financialsecrecyindex.com/). Not in original data.
overseas_territory | Boolean | True if country of incorporation is a British Overseas territory. Not in original data.
crown_dependency | Boolean | True if country of incorporation is a British Crown Dependency. Not in original data.

