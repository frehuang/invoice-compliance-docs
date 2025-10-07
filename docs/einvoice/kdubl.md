
# UBL 2.1 发票对象字段说明（带目录）

本文件依据以下标准生成：
- **UBL 2.1 Invoice** 官方定义
- **Peppol BIS Billing 3.0** 第 11 章
- **Pagero PUF Billing 2.0** 第 3 章

来源：发票统一数据结构（Excel）
组织方式：按“类别”分组。每个字段包含名称、描述、UBL XPath、是否必填及示例。

---

# 目录 (Table of Contents)
- [基础数据](#基础数据)
  - [CustomizationID](#customizationid)
  - [ProfileID](#profileid)
  - [ID](#id)
  - [UUID](#uuid)
  - [IssueDate](#issuedate)
  - [IssueTime](#issuetime)
  - [DueDate](#duedate)
  - [InvoiceTypeCode](#invoicetypecode)
  - [Note](#note)
  - [TaxPointDate](#taxpointdate)
  - [DocumentCurrencyCode](#documentcurrencycode)
  - [TaxCurrencyCode](#taxcurrencycode)
  - [InvoicePeriod](#invoiceperiod)
  - [StartDate](#startdate)
  - [EndDate](#enddate)
  - [DescriptionCode](#descriptioncode)
  - [Description](#description)
  - [BuyerReference](#buyerreference)
- [关联文档](#关联文档)
  - [OrderReference](#orderreference)
  - [ID](#id)
  - [BillingReference](#billingreference)
  - [InvoiceDocumentReference](#invoicedocumentreference)
  - [ID](#id)
  - [IssueDate](#issuedate)
  - [AdditionalDocumentReference](#additionaldocumentreference)
  - [ID](#id)
  - [DocumentDescription](#documentdescription)
  - [Attachment](#attachment)
  - [EmbeddedDocumentBinaryObject](#embeddeddocumentbinaryobject)
  - [ExternalReference](#externalreference)
  - [URI](#uri)
- [发票基础数据扩展](#发票基础数据扩展)
  - [InvoiceContext](#invoicecontext)
  - [SelfBilled](#selfbilled)
  - [InvoiceSubType](#invoicesubtype)
  - [InvoiceNumber](#invoicenumber)
  - [InvoiceCode](#invoicecode)
- [供应商信息](#供应商信息)
  - [AccountingSupplierParty](#accountingsupplierparty)
  - [CustomerAssignedAccountID](#customerassignedaccountid)
  - [Party](#party)
  - [EndpointID](#endpointid)
  - [EndpointID.schemeID](#endpointid-schemeid)
  - [IndustryClassificationCode](#industryclassificationcode)
  - [PartyIdentification.ID](#partyidentification-id)
  - [PartyIdentification.ID.schemeID](#partyidentification-id-schemeid)
  - [PartyName.Name](#partyname-name)
  - [Party.PostalAddress](#party-postaladdress)
  - [StreetName](#streetname)
  - [CityName](#cityname)
  - [CountrySubentity](#countrysubentity)
  - [PostalZone](#postalzone)
  - [Country.IdentificationCode](#country-identificationcode)
  - [Country.Name](#country-name)
  - [PartyTaxScheme](#partytaxscheme)
  - [TaxScheme.ID](#taxscheme-id)
  - [CompanyID](#companyid)
  - [Party.PartyLegalEntity](#party-partylegalentity)
  - [RegistrationName](#registrationname)
  - [CompanyID](#companyid)
  - [CompanyID.schemeID](#companyid-schemeid)
  - [CompanyLegalForm](#companylegalform)
  - [Party.RegistrationAddress](#party-registrationaddress)
  - [CityName](#cityname)
  - [Country](#country)
  - [IdentificationCode](#identificationcode)
  - [Party.Contact](#party-contact)
  - [Name](#name)
  - [Telephone](#telephone)
  - [ElectronicMail](#electronicmail)
  - [Party.Person](#party-person)
  - [FirstName](#firstname)
  - [FamilyName](#familyname)
  - [AccountingContact](#accountingcontact)
  - [Name](#name)
  - [Telephone](#telephone)
  - [Telefax](#telefax)
  - [ElectronicMail](#electronicmail)
- [角色信息: 客户
（接收发票的客户）](#角色信息-客户-接收发票的客户)
  - [AccountingCustomerParty](#accountingcustomerparty)
  - [SupplierAssignedAccountID](#supplierassignedaccountid)
  - [Party](#party)
  - [EndpointID](#endpointid)
  - [EndpointID.schemeID](#endpointid-schemeid)
  - [PartyIdentification.ID](#partyidentification-id)
  - [PartyIdentification.ID.schemeID](#partyidentification-id-schemeid)
  - [PartyName.Name](#partyname-name)
  - [Party.PostalAddress](#party-postaladdress)
  - [Postbox](#postbox)
  - [StreetName](#streetname)
  - [AdditionalStreetName](#additionalstreetname)
  - [BuildingNumber](#buildingnumber)
  - [Department](#department)
  - [PlotIdentification](#plotidentification)
  - [CitySubdivisionName](#citysubdivisionname)
  - [CityName](#cityname)
  - [PostalZone](#postalzone)
  - [CountrySubentity](#countrysubentity)
  - [AddressLine](#addressline)
  - [Line](#line)
  - [Country.IdentificationCode](#country-identificationcode)
  - [Country.Name](#country-name)
  - [PartyTaxScheme](#partytaxscheme)
  - [TaxScheme.ID](#taxscheme-id)
  - [CompanyID](#companyid)
  - [Party.PartyLegalEntity](#party-partylegalentity)
  - [RegistrationName](#registrationname)
  - [CompanyID](#companyid)
  - [CompanyID.schemeID](#companyid-schemeid)
  - [CompanyLegalForm](#companylegalform)
  - [Party.Contact](#party-contact)
  - [Name](#name)
  - [Telephone](#telephone)
  - [ElectronicMail](#electronicmail)
  - [Party.Person](#party-person)
  - [FirstName](#firstname)
  - [FamilyName](#familyname)
  - [AccountingContact](#accountingcontact)
  - [Name](#name)
  - [Telephone](#telephone)
  - [Telefax](#telefax)
  - [ElectronicMail](#electronicmail)
- [角色信息: 客户
（实际购买方）](#角色信息-客户-实际购买方)
  - [BuyerCustomerParty](#buyercustomerparty)
  - [AccountingCustomerParty一样）](#accountingcustomerparty一样)
- [角色信息: 税代信息](#角色信息-税代信息)
  - [TaxRepresentativeParty](#taxrepresentativeparty)
  - [Party](#party)
  - [PartyName.Name](#partyname-name)
  - [Party.PostalAddress](#party-postaladdress)
  - [StreetName](#streetname)
  - [CityName](#cityname)
  - [PostalZone](#postalzone)
  - [AddressLine](#addressline)
  - [Line](#line)
  - [Country.IdentificationCode](#country-identificationcode)
  - [PartyTaxScheme](#partytaxscheme)
  - [TaxScheme.ID](#taxscheme-id)
  - [CompanyID](#companyid)
- [物流信息：交货信息](#物流信息-交货信息)
  - [Delivery](#delivery)
  - [ActualDeliveryDate](#actualdeliverydate)
  - [LatestDeliveryDate](#latestdeliverydate)
  - [DeliveryLocation.ID](#deliverylocation-id)
  - [DeliveryLocation.ID.schemeID](#deliverylocation-id-schemeid)
  - [DeliveryLocation.Description](#deliverylocation-description)
  - [DeliveryLocation.Address.Postbox](#deliverylocation-address-postbox)
  - [DeliveryLocation.Address.Floor](#deliverylocation-address-floor)
  - [DeliveryLocation.Address.Room](#deliverylocation-address-room)
  - [DeliveryLocation.Address.StreetName](#deliverylocation-address-streetname)
  - [DeliveryLocation.Address.AdditionalStreetName](#deliverylocation-address-additionalstreetname)
  - [DeliveryLocation.Address.CityName](#deliverylocation-address-cityname)
  - [DeliveryLocation.Address.PostalZone](#deliverylocation-address-postalzone)
  - [DeliveryLocation.Address.Country.IdentificationCode](#deliverylocation-address-country-identificationcode)
  - [DeliveryLocation.Country.Name](#deliverylocation-country-name)
  - [CarrierParty.PartyName.Name](#carrierparty-partyname-name)
  - [DeliveryParty.PartyName.Name](#deliveryparty-partyname-name)
  - [DeliveryParty.Contact.Name](#deliveryparty-contact-name)
  - [DeliveryParty.Contact.Telephone](#deliveryparty-contact-telephone)
  - [DeliveryParty.Contact.ElectronicMail](#deliveryparty-contact-electronicmail)
- [物流信息：交货条款](#物流信息-交货条款)
  - [DeliveryTerms](#deliveryterms)
  - [ID](#id)
  - [SpecialTerms](#specialterms)
  - [LossRiskResponsibilityCode](#lossriskresponsibilitycode)
  - [LossRisk](#lossrisk)
- [付款：付款方式](#付款-付款方式)
  - [PaymentMeans](#paymentmeans)
  - [PaymentMeansCode](#paymentmeanscode)
  - [PaymentMeansCode.name](#paymentmeanscode-name)
  - [PaymentID](#paymentid)
  - [CardAccount.PrimaryAccountNumberID](#cardaccount-primaryaccountnumberid)
  - [CardAccount.NetworkID](#cardaccount-networkid)
  - [CardAccount.HolderName](#cardaccount-holdername)
  - [PayeeFinancialAccount.ID](#payeefinancialaccount-id)
  - [PayeeFinancialAccount.Name](#payeefinancialaccount-name)
  - [PayeeFinancialAccount.CurrencyCode](#payeefinancialaccount-currencycode)
  - [PayeeFinancialAccount.FinancialInstitutionBranch.ID](#payeefinancialaccount-financialinstitutionbranch-id)
  - [PayeeFinancialAccount.FinancialInstitutionBranch.Name](#payeefinancialaccount-financialinstitutionbranch-name)
  - [PayeeFinancialAccount.FinancialInstitutionBranch.Address.Postbox](#payeefinancialaccount-financialinstitutionbranch-address-postbox)
  - [PayeeFinancialAccount.FinancialInstitutionBranch.Address.Floor](#payeefinancialaccount-financialinstitutionbranch-address-floor)
  - [PayeeFinancialAccount.FinancialInstitutionBranch.Address.Room](#payeefinancialaccount-financialinstitutionbranch-address-room)
  - [PayeeFinancialAccount.FinancialInstitutionBranch.Address.StreetName](#payeefinancialaccount-financialinstitutionbranch-address-streetname)
  - [PayeeFinancialAccount.FinancialInstitutionBranch.Address.CityName](#payeefinancialaccount-financialinstitutionbranch-address-cityname)
  - [PayeeFinancialAccount.FinancialInstitutionBranch.Address.Country.IdentificationCode](#payeefinancialaccount-financialinstitutionbranch-address-country-identificationcode)
  - [PaymentMandate.ID](#paymentmandate-id)
  - [PaymentMandate.PayerFinancialAccount.ID](#paymentmandate-payerfinancialaccount-id)
- [付款：付款条件](#付款-付款条件)
  - [PaymentTerms](#paymentterms)
  - [Note](#note)
  - [PenaltySurchargePercent](#penaltysurchargepercent)
- [付款：预付款](#付款-预付款)
  - [PrepaidPayment](#prepaidpayment)
  - [PaidAmount](#paidamount)
  - [PaidAmount.currencyID](#paidamount-currencyid)
- [折扣及附加费用](#折扣及附加费用)
  - [AllowanceCharge](#allowancecharge)
  - [ChargeIndicator](#chargeindicator)
  - [AllowanceChargeReasonCode](#allowancechargereasoncode)
  - [AllowanceChargeReason](#allowancechargereason)
  - [MultiplierFactorNumeric](#multiplierfactornumeric)
  - [Amount](#amount)
  - [Amount.currencyID](#amount-currencyid)
  - [BaseAmount](#baseamount)
  - [BaseAmount.currencyID](#baseamount-currencyid)
  - [TaxCategory.ID](#taxcategory-id)
  - [TaxCategory.Percent](#taxcategory-percent)
  - [TaxCategory.TaxExemptionReasonCode](#taxcategory-taxexemptionreasoncode)
  - [TaxCategory.TaxExemptionReason](#taxcategory-taxexemptionreason)
  - [TaxCategory.TaxScheme.ID](#taxcategory-taxscheme-id)
  - [TaxTotal.TaxAmount](#taxtotal-taxamount)
  - [TaxTotal.TaxAmount.currencyID](#taxtotal-taxamount-currencyid)
- [税：税收汇率](#税-税收汇率)
  - [TaxExchangeRate](#taxexchangerate)
  - [SourceCurrencyCode](#sourcecurrencycode)
  - [TargetCurrencyCode](#targetcurrencycode)
  - [CalculationRate](#calculationrate)
  - [MathematicOperatorCode](#mathematicoperatorcode)
  - [Date](#date)
- [税：总税额](#税-总税额)
  - [TaxTotal](#taxtotal)
  - [TaxAmount](#taxamount)
  - [TaxAmount.currencyID](#taxamount-currencyid)
  - [TaxSubtotal](#taxsubtotal)
  - [TaxSubtotal.TaxableAmount](#taxsubtotal-taxableamount)
  - [TaxSubtotal.TaxableAmount.currencyID](#taxsubtotal-taxableamount-currencyid)
  - [TaxSubtotal.TaxAmount](#taxsubtotal-taxamount)
  - [TaxSubtotal.TaxAmount.currencyID](#taxsubtotal-taxamount-currencyid)
  - [TaxSubtotal.TaxCategory.ID](#taxsubtotal-taxcategory-id)
  - [TaxSubtotal.TaxCategory.Percent](#taxsubtotal-taxcategory-percent)
  - [TaxSubtotal.TaxCategory.TaxExemptionReasonCode](#taxsubtotal-taxcategory-taxexemptionreasoncode)
  - [TaxSubtotal.TaxCategory.TaxExemptionReason](#taxsubtotal-taxcategory-taxexemptionreason)
  - [TaxSubtotal.TaxCategory.TaxScheme.ID](#taxsubtotal-taxcategory-taxscheme-id)
  - [TaxSubtotal.TaxCategory.TaxScheme.Name](#taxsubtotal-taxcategory-taxscheme-name)
- [税：预扣税](#税-预扣税)
  - [WithholdingTaxTotal](#withholdingtaxtotal)
  - [TaxAmount](#taxamount)
  - [TaxAmount.currencyID](#taxamount-currencyid)
  - [TaxSubtotal.TaxableAmount](#taxsubtotal-taxableamount)
  - [TaxSubtotal.TaxAmount](#taxsubtotal-taxamount)
  - [TaxSubtotal.TaxCategory.ID](#taxsubtotal-taxcategory-id)
  - [TaxSubtotal.TaxCategory.Percent](#taxsubtotal-taxcategory-percent)
  - [TaxSubtotal.TaxCategory.TaxScheme.ID](#taxsubtotal-taxcategory-taxscheme-id)
  - [TaxSubtotal.TaxCategory.TaxScheme.Name](#taxsubtotal-taxcategory-taxscheme-name)
  - [WithholdingTaxTotal](#withholdingtaxtotal)
  - [TaxAmount](#taxamount)
  - [TaxAmount.currencyID](#taxamount-currencyid)
  - [TaxSubtotal.TaxableAmount](#taxsubtotal-taxableamount)
  - [TaxSubtotal.TaxableAmount.currencyID](#taxsubtotal-taxableamount-currencyid)
  - [TaxSubtotal.TaxAmount](#taxsubtotal-taxamount)
  - [TaxSubtotal.TaxAmount.currencyID](#taxsubtotal-taxamount-currencyid)
  - [TaxSubtotal.TaxCategory.ID](#taxsubtotal-taxcategory-id)
  - [TaxSubtotal.TaxCategory.Percent](#taxsubtotal-taxcategory-percent)
  - [TaxSubtotal.TaxCategory.TaxExemptionReasonCode](#taxsubtotal-taxcategory-taxexemptionreasoncode)
  - [TaxSubtotal.TaxCategory.TaxExemptionReason](#taxsubtotal-taxcategory-taxexemptionreason)
  - [TaxSubtotal.TaxCategory.TaxScheme.ID](#taxsubtotal-taxcategory-taxscheme-id)
- [发票上法律
要求的总金额信息](#发票上法律-要求的总金额信息)
  - [LegalMonetaryTotal](#legalmonetarytotal)
  - [LineExtensionAmount](#lineextensionamount)
  - [LineExtensionAmount.currencyID](#lineextensionamount-currencyid)
  - [TaxExclusiveAmount](#taxexclusiveamount)
  - [TaxExclusiveAmount.currencyID](#taxexclusiveamount-currencyid)
  - [TaxInclusiveAmount](#taxinclusiveamount)
  - [TaxInclusiveAmount.currencyID](#taxinclusiveamount-currencyid)
  - [AllowanceTotalAmount](#allowancetotalamount)
  - [AllowanceTotalAmount.currencyID](#allowancetotalamount-currencyid)
  - [ChargeTotalAmount](#chargetotalamount)
  - [ChargeTotalAmount.currencyID](#chargetotalamount-currencyid)
  - [PrepaidAmount](#prepaidamount)
  - [PrepaidAmount.currencyID](#prepaidamount-currencyid)
  - [PayableRoundingAmount](#payableroundingamount)
  - [PayableRoundingAmount.currencyID](#payableroundingamount-currencyid)
  - [PayableAmount](#payableamount)
  - [PayableAmount.currencyID](#payableamount-currencyid)
  - [InvoiceLine](#invoiceline)
  - [ID](#id)
  - [Note](#note)
  - [InvoicedQuantity](#invoicedquantity)
  - [InvoicedQuantity.unitCode](#invoicedquantity-unitcode)
  - [LineExtensionAmount](#lineextensionamount)
  - [LineExtensionAmount.currencyID](#lineextensionamount-currencyid)
  - [AccountingCost](#accountingcost)
  - [InvoicePeriod](#invoiceperiod)
  - [StartDate](#startdate)
  - [EndDate](#enddate)
- [行基础数据：
开票项信息](#行基础数据-开票项信息)
  - [Item](#item)
  - [Description](#description)
  - [Name](#name)
  - [BuyersItemIdentification](#buyersitemidentification)
  - [BuyersItemIdentification.ID](#buyersitemidentification-id)
  - [SellersItemIdentification](#sellersitemidentification)
  - [SellersItemIdentification.ID](#sellersitemidentification-id)
  - [ManufacturersItemIdentification](#manufacturersitemidentification)
  - [ManufacturersItemIdentification.ID](#manufacturersitemidentification-id)
  - [StandardItemIdentification](#standarditemidentification)
  - [StandardItemIdentification.ID](#standarditemidentification-id)
  - [StandardItemIdentification.ID.schemeID](#standarditemidentification-id-schemeid)
  - [OriginCountry](#origincountry)
  - [OriginCountry.IdentificationCode](#origincountry-identificationcode)
  - [CommodityClassification](#commodityclassification)
  - [CommodityClassification.ItemClassificationCode](#commodityclassification-itemclassificationcode)
  - [CommodityClassification.ItemClassificationCode.listID](#commodityclassification-itemclassificationcode-listid)
  - [CommodityClassification.ItemClassificationCode.listVersionID](#commodityclassification-itemclassificationcode-listversionid)
  - [ClassifiedTaxCategory](#classifiedtaxcategory)
  - [ClassifiedTaxCategory.ID](#classifiedtaxcategory-id)
  - [ClassifiedTaxCategory.ID.schemeID](#classifiedtaxcategory-id-schemeid)
  - [ClassifiedTaxCategory.Percent](#classifiedtaxcategory-percent)
  - [ClassifiedTaxCategory.TaxScheme.ID](#classifiedtaxcategory-taxscheme-id)
  - [AdditionalItemProperty](#additionalitemproperty)
  - [AdditionalItemProperty.Name](#additionalitemproperty-name)
  - [AdditionalItemProperty.Value](#additionalitemproperty-value)
  - [ItemInstance](#iteminstance)
  - [ItemInstance.ManufactureDate](#iteminstance-manufacturedate)
  - [ItemInstance.BestBeforeDate](#iteminstance-bestbeforedate)
  - [ItemInstance.SerialID](#iteminstance-serialid)
  - [ItemInstance.LotIdentification.LotNumberID](#iteminstance-lotidentification-lotnumberid)
  - [ItemInstance.LotIdentification.ExpiryDate](#iteminstance-lotidentification-expirydate)
- [行基础数据：价格](#行基础数据-价格)
  - [Price](#price)
  - [PriceAmount](#priceamount)
  - [PriceAmount.currencyID](#priceamount-currencyid)
  - [BaseQuantity](#basequantity)
  - [BaseQuantity.unitCode](#basequantity-unitcode)
  - [AllowanceCharge](#allowancecharge)
  - [AllowanceCharge.ChargeIndicator](#allowancecharge-chargeindicator)
  - [AllowanceCharge.Amount](#allowancecharge-amount)
  - [AllowanceCharge.Amount.currencyID](#allowancecharge-amount-currencyid)
  - [AllowanceCharge.BaseAmount](#allowancecharge-baseamount)
  - [AllowanceCharge.BaseAmount.currencyID](#allowancecharge-baseamount-currencyid)
- [行基础数据：
折扣或附加费](#行基础数据-折扣或附加费)
  - [AllowanceCharge](#allowancecharge)
  - [ChargeIndicator](#chargeindicator)
  - [AllowanceChargeReasonCode](#allowancechargereasoncode)
  - [AllowanceChargeReason](#allowancechargereason)
  - [MultiplierFactorNumeric](#multiplierfactornumeric)
  - [Amount](#amount)
  - [Amount.currencyID](#amount-currencyid)
  - [BaseAmount](#baseamount)
  - [BaseAmount.currencyID](#baseamount-currencyid)
- [税](#税)
  - [TaxTotal](#taxtotal)
  - [TaxAmount](#taxamount)
  - [TaxAmount.currencyID](#taxamount-currencyid)
  - [TaxSubtotal](#taxsubtotal)
  - [TaxSubtotal.TaxableAmount](#taxsubtotal-taxableamount)
  - [TaxSubtotal.TaxableAmount.currencyID](#taxsubtotal-taxableamount-currencyid)
  - [TaxSubtotal.TaxAmount](#taxsubtotal-taxamount)
  - [TaxSubtotal.TaxAmount.currencyID](#taxsubtotal-taxamount-currencyid)
  - [TaxSubtotal.TaxCategory.ID](#taxsubtotal-taxcategory-id)
  - [TaxSubtotal.TaxCategory.Percent](#taxsubtotal-taxcategory-percent)
  - [TaxSubtotal.TaxCategory.TaxExemptionReasonCode](#taxsubtotal-taxcategory-taxexemptionreasoncode)
  - [TaxSubtotal.TaxCategory.TaxExemptionReason](#taxsubtotal-taxcategory-taxexemptionreason)
  - [TaxSubtotal.TaxCategory.TaxScheme.ID](#taxsubtotal-taxcategory-taxscheme-id)
- [附件](#附件)
  - [DocumentReference](#documentreference)
  - [ID](#id)
  - [ID.schemeID](#id-schemeid)
  - [IssueDate](#issuedate)
  - [IssueTime](#issuetime)
  - [DocumentTypeCode](#documenttypecode)

---

## 基础数据

### CustomizationID
- **描述**：文档规格标识符，必须为值 'urn:piaozone.com:ubl-2.1-customizations:v1.0'
- **UBL XPath**：`cbc:CustomizationID`
- **是否必填**：必填
- **示例**：
```xml
<cbc:CustomizationID>urn:piaozone.com:ubl-2.1-customizations:v1.0</cbc:CustomizationID>
```


### ProfileID
- **描述**：识别业务流程，必须为值 'urn:www.piaozone.com:profile:bill:v1.0'
- **UBL XPath**：`cbc:ProfileID`
- **是否必填**：必填
- **示例**：
```xml
<cbc:ProfileID>urn:www.piaozone.com:profile:bill:v1.0</cbc:ProfileID>
```


### ID
- **描述**：发票的唯一标识符。
- **UBL XPath**：`cbc:ID`
- **是否必填**：必填
- **示例**：
```xml
<cbc:ID>51234882</cbc:ID>
```


### UUID
- **描述**：文档标识符，与 SBDH 中的 InstanceIdentifier（传输 ID）不同
- **UBL XPath**：`cbc:UUID`

### IssueDate
- **描述**：发票的签发日期，格式为 "YYYY-MM-DD"
- **UBL XPath**：`cbc:IssueDate`
- **是否必填**：必填
- **示例**：
```xml
<cbc:IssueDate>2021-01-30</cbc:IssueDate>
```


### IssueTime
- **描述**：发票的签发时间，格式为 "HH:mm:ss", "HH:mm:ssZZZZ", "HH:mm:ss.SSS’Z'" 或 "HH:mm:ss.SSS"
- **UBL XPath**：`cbc:IssueTime`
- **是否必填**：否
- **示例**：
```xml
<cbc:IssueTime>21:32:52</cbc:IssueTime>
```


### DueDate
- **描述**：发票的到期日期，格式为 "YYYY-MM-DD"，CreditNote不传改节点；
Peppol国家，一般该字段和付款条件2者必填一
- **UBL XPath**：`cbc:DueDate`
- **是否必填**：按实际情况必填
- **示例**：
```xml
<cbc:DueDate>2021-02-28</cbc:DueDate>
```


### InvoiceTypeCode
- **描述**：发票类型代码。示例值 '380' 表示Invoice，示例值 '381' 表示CreditNote
- **UBL XPath**：`cbc:InvoiceTypeCode`
- **是否必填**：必填
- **示例**：
```xml
<cbc:InvoiceTypeCode>380</cbc:InvoiceTypeCode>
```


### Note
- **描述**：备注，可多次多次重复，表示自由文本。
- **UBL XPath**：`cbc:Note`
- **是否必填**：否
- **示例**：
```xml
<Invoice>
  <cbc:Note>This</cbc:Note>
  <cbc:Note>is a</cbc:Note>
  <cbc:Note>free text example</cbc:Note>
</Invoice>
```


### TaxPointDate
- **描述**：增值税应税日期，如果税收应税日期与发票签发日期不同，则填写，格式为 "YYYY-MM-DD"。
一般来说，应税日期是增值税（VAT）目的上的交易发生日期。它是卖方和买方应为增值税负责的日期，前提是该日期可以确定，并且与发票签发日期不同。如果卖方和买方的增值税责任日期与发票签发日期不同，则此元素为必填项，应填写该日期。
- **UBL XPath**：`cbc:TaxPointDate`
- **是否必填**：否
- **示例**：
```xml
<cbc:TaxPointDate>2021-01-31</cbc:TaxPointDate>
```


### DocumentCurrencyCode
- **描述**：发票中的货币代码，需符合ISO 4217货币代码。
发票中指定金额的货币代码，除了以记账货币表示的总增值税金额外。此外，发票中只能使用一种货币，记账货币代码和发票总增值税金额的记账货币代码除外
- **UBL XPath**：`cbc:DocumentCurrencyCode`
- **是否必填**：必填
- **示例**：
```xml
<cbc:DocumentCurrencyCode>EUR</cbc:DocumentCurrencyCode>
```


### TaxCurrencyCode
- **描述**：税务货币代码，若发票中的金额与账务货币不同，则需填写。
用于增值税记账和报告的货币，必须是卖方所在国接受或要求的货币。当增值税记账货币代码与发票货币代码不同时，应与发票总增值税金额一起使用。
- **UBL XPath**：`cbc:TaxCurrencyCode`
- **是否必填**：按实际情况必填
- **示例**：
```xml
<cbc:TaxCurrencyCode>USD</cbc:TaxCurrencyCode>
```


### InvoicePeriod
- **描述**：发票期间信息，包含开始日期、结束日期和描述。
- **UBL XPath**：`cac:InvoicePeriod`
- **是否必填**：否

### StartDate
- **描述**：发票期间的开始日期，格式为 "YYYY-MM-DD"
- **UBL XPath**：`cbc:StartDate`
- **是否必填**：父节点存在则必填

### EndDate
- **描述**：发票期间的结束日期，格式为 "YYYY-MM-DD"
- **UBL XPath**：`cbc:EndDate`
- **是否必填**：父节点存在则必填

### DescriptionCode
- **描述**：3:Invoice document issue date time ;35: Delivery date/time, actual ;432: Paid to date
- **UBL XPath**：`cbc:DescriptionCode`
- **是否必填**：父节点存在则必填

### Description
- **描述**：发票期间描述，表示自由文本
- **UBL XPath**：`cbc:Description`
- **是否必填**：父节点存在则必填

### BuyerReference
- **描述**：由买方提供的、用于文档内部传递（流转）的引用信息。Peppol国家，BuyerReference和OrderReference两者必填一项
- **UBL XPath**：`cbc:BuyerReference`
- **是否必填**：按实际情况必填


## 关联文档

### OrderReference
- **描述**：关联订单号
- **UBL XPath**：`cac:OrderReference`
- **是否必填**：按实际情况必填
- **示例**：
```xml
<cac:OrderReference>
        <cbc:ID>order 123</cbc:ID>
    </cac:OrderReference>
```


### ID
- **UBL XPath**：`cbc:ID`
- **是否必填**：按实际情况必填

### BillingReference
- **描述**：红票必填
- **UBL XPath**：`cac:BillingReference`
- **是否必填**：按实际情况必填
- **示例**：
```xml
<cac:BillingReference>
			<cac:InvoiceDocumentReference>
				<cbc:ID>INV0001</cbc:ID>
				<cbc:IssueDate>2024-06-01</cbc:IssueDate>
			</cac:InvoiceDocumentReference>
		</cac:BillingReference>
```


### InvoiceDocumentReference
- **描述**：关联发票文件 (Reference to related invoice document)
- **UBL XPath**：`cac:InvoiceDocumentReference`
- **是否必填**：按实际情况必填

### ID
- **描述**：原蓝字发票号码
- **UBL XPath**：`cbc:ID`
- **是否必填**：按实际情况必填

### IssueDate
- **描述**：原蓝字发票日期
- **UBL XPath**：`cbc:IssueDate`
- **是否必填**：按实际情况必填

### AdditionalDocumentReference
- **描述**：附件
- **UBL XPath**：`cac:AdditionalDocumentReference`
- **是否必填**：否
- **示例**：
```xml
<cac:AdditionalDocumentReference>
        <cbc:ID>doc1</cbc:ID>
        <cbc:DocumentDescription>Usage breakdown</cbc:DocumentDescription>
        <cac:Attachment>
            <cac:ExternalReference>
                <cbc:URI>http://www.salescompany.be/breakdown001.html</cbc:URI>
            </cac:ExternalReference>
        </cac:Attachment>
    </cac:AdditionalDocumentReference>

    <cac:AdditionalDocumentReference>
        <cbc:ID>doc2</cbc:ID>
        <cbc:DocumentDescription>Usage summary</cbc:DocumentDescription>
        <cac:Attachment>
            <cbc:EmbeddedDocumentBinaryObject filename="report.csv" mimeCode="text/csv">
                aHR0cHM6Ly90ZXN0LXZlZmEuZGlmaS5uby9wZXBwb2xiaXMvcG9hY2MvYmlsbGluZy8zLjAvYmlzLw==
            </cbc:EmbeddedDocumentBinaryObject>
        </cac:Attachment>
    </cac:AdditionalDocumentReference>
```


### ID
- **UBL XPath**：`cbc:ID`
- **是否必填**：否

### DocumentDescription
- **描述**：文件描述 (Description of document content)
- **UBL XPath**：`cbc:DocumentDescription`
- **是否必填**：否

### Attachment
- **描述**：附件 (Attached file or document)
- **UBL XPath**：`cac:Attachment`
- **是否必填**：否

### EmbeddedDocumentBinaryObject
- **描述**：附件内容
- **UBL XPath**：`cbc:EmbeddedDocumentBinaryObject`
- **是否必填**：否

### ExternalReference
- **描述**：外部参考 (Reference to external document)
- **UBL XPath**：`cac:ExternalReference`
- **是否必填**：否

### URI
- **描述**：附件链接
- **UBL XPath**：`cbc:URI`
- **是否必填**：否


## 发票基础数据扩展

### InvoiceContext
- **描述**：开票类型，不同国家代表不同意义。开票业务的上下文信息
- **UBL XPath**：`cac:AdditionalDocumentReference
[cbc:DocumentType='InvoiceContext']
    /cbc:ID`
- **是否必填**：按实际情况必填

### SelfBilled
- **描述**：是否反向开票
- **UBL XPath**：`cac:AdditionalDocumentReference
[cbc:DocumentType='SelfBilled']
    /cbc:ID`
- **是否必填**：按实际情况必填

### InvoiceSubType
- **描述**：发票种类，当地国家定义的发票类型
- **UBL XPath**：`cac:AdditionalDocumentReference
[cbc:DocumentType='InvoiceSubType']
    /cbc:ID`
- **是否必填**：按实际情况必填

### InvoiceNumber
- **描述**：发票号码，仅使用在中国金三发票、越南、印尼、土耳其
- **UBL XPath**：`cac:AdditionalDocumentReference
[cbc:DocumentType='InvoiceNumber']
    /cbc:ID`
- **是否必填**：按实际情况必填

### InvoiceCode
- **描述**：发票号码，仅使用在中国金三发票、越南、印尼、土耳其
- **UBL XPath**：`cac:AdditionalDocumentReference
[cbc:DocumentType='InvoiceCode']
    /cbc:ID`
- **是否必填**：按实际情况必填


## 供应商信息

### AccountingSupplierParty
- **描述**：供应商相关信息
- **UBL XPath**：`cac:AccountingSupplierParty`
- **是否必填**：必填
- **示例**：
```xml
<Invoice>
  <!-- Code omitted for clarity -->
  <cac:AccountingSupplierParty>
      <cbc:CustomerAssignedAccountID>SupplierId</cbc:CustomerAssignedAccountID>
      <cac:Party>
          <cbc:EndpointID schemeID="0088">7300010000001</cbc:EndpointID>
          <cac:PartyIdentification>
              <cbc:ID schemeID="0088">7300010000001</cbc:ID>
          </cac:PartyIdentification>
          <cac:PartyName>
              <cbc:Name>Supplier Name</cbc:Name>
          </cac:PartyName>
          <cac:PostalAddress>
              <cbc:Postbox>12345</cbc:Postbox>
              <cbc:StreetName>Test Street 1</cbc:StreetName>
              <cbc:Department>Department</cbc:Department>
              <cbc:PlotIdentification>0000</cbc:PlotIdentification>
              <cbc:CitySubdivisionName>City Subdivision Name</cbc:CitySubdivisionName>
              <cbc:CityName>Town</cbc:CityName>
              <cbc:PostalZone>00000</cbc:PostalZone>
              <cbc:CountrySubentity>Province</cbc:CountrySubentity>
              <cac:Country>
                  <cbc:IdentificationCode>SE</cbc:IdentificationCode>
                  <cbc:Name>Sweden</cbc:Name>
              </cac:Country>
          </cac:PostalAddress>
          <cac:PartyTaxScheme>
              <cbc:CompanyID>SE123456123401</cbc:CompanyID>
              <cac:TaxScheme>
                  <cbc:ID>VAT</cbc:ID>
              </cac:TaxScheme>
          </cac:PartyTaxScheme>
          <cac:PartyLegalEntity>
              <cbc:RegistrationName>Supplier Registration Name</cbc:RegistrationName>
              <cbc:CompanyID schemeID="0007">1234561234</cbc:CompanyID>
              <cac:RegistrationAddress>
                  <cbc:CityName>Supplier Hometown</cbc:CityName>
                  <cac:Country>
                      <cbc:IdentificationCode>SE</cbc:IdentificationCode>
                  </cac:Country>
              </cac:RegistrationAddress>
          </cac:PartyLegalEntity>
          <cac:Contact>
              <cbc:Name>Supplier Contact Name</cbc:Name>
              <cbc:Telephone>11111111</cbc:Telephone>
              <cbc:ElectronicMail>supplier@contact.com</cbc:ElectronicMail>
          </cac:Contact>
      </cac:Party>
      <cac:AccountingContact>
          <cbc:Name>Supplier Accounting Name</cbc:Name>
          <cbc:Telephone>Supplier Tel</cbc:Telephone>
          <cbc:Telefax>Supplier Fax</cbc:Telefax>
          <cbc:ElectronicMail>Supplier@mainContact.com</cbc:ElectronicMail>
      </cac:AccountingContact>
  </cac:AccountingSupplierParty>
  <!-- Code omitted for clarity -->
</Invoice>
```


### CustomerAssignedAccountID
- **描述**：购方分配的供应商编号
- **UBL XPath**：`cbc:CustomerAssignedAccountID`
- **是否必填**：否

### Party
- **描述**：供应商基础信息
- **UBL XPath**：`cac:Party`
- **是否必填**：必填

### EndpointID
- **描述**：标识供应商的电子通信路径，可以是：PEPPOLID, 电子邮件地址，EDI 地址，其他数字标识符
- **UBL XPath**：`cbc:EndpointID`
- **是否必填**：否

### EndpointID.schemeID
- **描述**：通信方式，mailto是指邮件方式
- **UBL XPath**：`cbc:EndpointID/@schemeID`
- **是否必填**：否

### IndustryClassificationCode
- **描述**：供应商的行业分类代码。
- **UBL XPath**：`cbc:IndustryClassificationCode`
- **是否必填**：否

### PartyIdentification.ID
- **描述**：父节点cac:PartyIdentification存在则必填，供应商的标识符
- **UBL XPath**：`cac:PartyIdentification/cbc:ID`
- **是否必填**：父节点存在则必填

### PartyIdentification.ID.schemeID
- **描述**：父节点cac:PartyIdentification存在则必填，
供应商标识符的模式标识符
- **UBL XPath**：`cac:PartyIdentification/cbc:ID/@schemeID`
- **是否必填**：父节点存在则必填

### PartyName.Name
- **描述**：供应商的名称
- **UBL XPath**：`cac:PartyName/cbc:Name`
- **是否必填**：选填

### Party.PostalAddress
- **描述**：邮政地址信息
- **UBL XPath**：`cac:Party/cac:PostalAddress`
- **是否必填**：选填

### StreetName
- **描述**：供应商的街道名称
- **UBL XPath**：`cbc:StreetName`
- **是否必填**：选填

### CityName
- **描述**：供应商的城市名称
- **UBL XPath**：`cbc:CityName`
- **是否必填**：选填

### CountrySubentity
- **描述**：省/州
- **UBL XPath**：`cbc:CountrySubentity`
- **是否必填**：选填

### PostalZone
- **描述**：供应商的邮政编码；Peppol系必填
- **UBL XPath**：`cbc:PostalZone`
- **是否必填**：必填

### Country.IdentificationCode
- **描述**：国家/地区的代码，使用来自 ISO3166-1标准的两位字母国家地区代码
- **UBL XPath**：`cac:Country/cbc:IdentificationCode`
- **是否必填**：必填

### Country.Name
- **描述**：国家/地区的名称
- **UBL XPath**：`cac:Country/cbc:Name`
- **是否必填**：否

### PartyTaxScheme
- **描述**：税务信息
- **UBL XPath**：`cac:PartyTaxScheme`
- **是否必填**：必填

### TaxScheme.ID
- **描述**：增值税标识符，使用“VAT”或 "GST"等
- **UBL XPath**：`cac:TaxScheme/cbc:ID`
- **是否必填**：必填

### CompanyID
- **描述**：卖方的增值税识别号，或为税务目的根据卖方地址定义的本地识别号，
或使卖方能够说明其注册税务状态的参考编号。
- **UBL XPath**：`cbc:CompanyID`
- **是否必填**：必填

### Party.PartyLegalEntity
- **描述**：法律实体相关信息
- **UBL XPath**：`cac:Party/cac:PartyLegalEntity`
- **是否必填**：必填

### RegistrationName
- **描述**：卖方的正式名称或公司名称
- **UBL XPath**：`cbc:RegistrationName`
- **是否必填**：必填

### CompanyID
- **描述**：由官方注册机构颁发的标识符，用于识别卖方为合法实体或个人。
为了让买方能够自动识别供应商，必须提供卖方标识符、卖方法律注册标识符和/或卖方增值税标识符。
该字段是可选的，但在大多数情况下应填写。
- **UBL XPath**：`cbc:CompanyID`
- **是否必填**：建议必填

### CompanyID.schemeID
- **描述**：卖方的法律注册标识符方案标识符
值必须符合代码列表
- **UBL XPath**：`cbc:CompanyID/@schemeID`
- **是否必填**：必填

### CompanyLegalForm
- **描述**：与卖方相关的其他法律信息
- **UBL XPath**：`cbc:CompanyLegalForm`
- **是否必填**：否

### Party.RegistrationAddress
- **描述**：注册地址
- **UBL XPath**：`cac:Party/cac:RegistrationAddress`
- **是否必填**：否

### CityName
- **描述**：注册地址城市名称
- **UBL XPath**：`cbc:CityName`
- **是否必填**：否

### Country
- **描述**：注册地址国家地区信息
- **UBL XPath**：`cac:Country`
- **是否必填**：否

### IdentificationCode
- **描述**：注册地址国家地区编码
- **UBL XPath**：`cbc:IdentificationCode`
- **是否必填**：否

### Party.Contact
- **描述**：联系方式
- **UBL XPath**：`cac:Party/cac:Contact`
- **是否必填**：建议必填

### Name
- **描述**：联系人名称
- **UBL XPath**：`cbc:Name`
- **是否必填**：建议必填

### Telephone
- **描述**：联系人电话
- **UBL XPath**：`cbc:Telephone`
- **是否必填**：否

### ElectronicMail
- **描述**：联系人电子邮件地址
- **UBL XPath**：`cbc:ElectronicMail`
- **是否必填**：建议必填

### Party.Person
- **描述**：如果卖方是个人，则应在特定元素中包含卖方的名字和姓氏。
- **UBL XPath**：`cac:Party/cac:Person`
- **是否必填**：按实际情况必填

### FirstName
- **描述**：个人的名字部分
- **UBL XPath**：`cbc:FirstName`
- **是否必填**：必填

### FamilyName
- **描述**：个人的姓氏
- **UBL XPath**：`cbc:FamilyName`
- **是否必填**：必填

### AccountingContact
- **描述**：会计联系人方式
- **UBL XPath**：`cac:AccountingContact`
- **是否必填**：否

### Name
- **描述**：会计联系人名称
- **UBL XPath**：`cbc:Name`
- **是否必填**：否

### Telephone
- **描述**：会计联系人电话
- **UBL XPath**：`cbc:Telephone`
- **是否必填**：否

### Telefax
- **描述**：会计联系人传真
- **UBL XPath**：`cbc:Telefax`
- **是否必填**：否

### ElectronicMail
- **描述**：会计联系人电子邮件地址
- **UBL XPath**：`cbc:ElectronicMail`
- **是否必填**：否


## 角色信息: 客户
（接收发票的客户）

### AccountingCustomerParty
- **描述**：买方信息
- **UBL XPath**：`cac:AccountingCustomerParty`
- **是否必填**：必填
- **示例**：
```xml
<Invoice>
  <!-- Code omitted for clarity -->
  <cac:AccountingCustomerParty>
      <cbc:SupplierAssignedAccountID>Customer Number</cbc:SupplierAssignedAccountID>
      <cac:Party>
          <cbc:EndpointID schemeID="0088">7300010000001</cbc:EndpointID>
          <cac:PartyIdentification>
              <cbc:ID schemeID="0088">7300010000001</cbc:ID>
          </cac:PartyIdentification>
          <cac:PartyName>
              <cbc:Name>Customer Name</cbc:Name>
          </cac:PartyName>
          <cac:PostalAddress>
              <cbc:Postbox>54321</cbc:Postbox>
              <cbc:StreetName>Customer Street</cbc:StreetName>
              <cbc:Department>Customer Department</cbc:Department>
              <cbc:PlotIdentification>0000</cbc:PlotIdentification>
              <cbc:CitySubdivisionName>Customer City Subdivision Name</cbc:CitySubdivisionName>
              <cbc:CityName>Customer City</cbc:CityName>
              <cbc:PostalZone>00000</cbc:PostalZone>
              <cbc:CountrySubentity>Customer Province</cbc:CountrySubentity>
	      <cac:AddressLine>
			<cbc:Line>1234 Elm Street</cbc:Line>
		</cac:AddressLine>
		<cac:AddressLine>
			<cbc:Line>Apartment 56B</cbc:Line>
		</cac:AddressLine>
              <cac:Country>
                  <cbc:IdentificationCode>SE</cbc:IdentificationCode>
                  <cbc:Name>Sweden</cbc:Name>
              </cac:Country>
          </cac:PostalAddress>
          <cac:PartyTaxScheme>
              <cbc:CompanyID>SE987654321001</cbc:CompanyID>
              <cac:TaxScheme>
                  <cbc:ID>VAT</cbc:ID>
              </cac:TaxScheme>
          </cac:PartyTaxScheme>
          <cac:PartyLegalEntity>
              <cbc:RegistrationName>Customer Registration Name</cbc:RegistrationName>
              <cbc:CompanyID schemeID="0007">987654-4321</cbc:CompanyID>
          </cac:PartyLegalEntity>
          <cac:Contact>
              <cbc:Name>Customer Contact Name</cbc:Name>
              <cbc:Telephone>+465544466</cbc:Telephone>
              <cbc:ElectronicMail>customer@contact.com</cbc:ElectronicMail>
          </cac:Contact>
      </cac:Party>
      <cac:AccountingContact>
          <cbc:Name>Customer Accounting Name</cbc:Name>
          <cbc:Telephone>Customer Tel</cbc:Telephone>
          <cbc:Telefax>Customer Fax</cbc:Telefax>
          <cbc:ElectronicMail>Customer@mainContact.com</cbc:ElectronicMail>
      </cac:AccountingContact>
  </cac:AccountingCustomerParty>
  <!-- Code omitted for clarity -->
</Invoice>
```


### SupplierAssignedAccountID
- **描述**：卖方分配的客户ID
- **UBL XPath**：`cbc:SupplierAssignedAccountID`
- **是否必填**：否

### Party
- **描述**：买方基础信息
- **UBL XPath**：`cac:Party`

### EndpointID
- **描述**：标识买方的电子通信路径，可以是：电子邮件地址，EDI 地址，其他数字标识符
- **UBL XPath**：`cbc:EndpointID`
- **是否必填**：否

### EndpointID.schemeID
- **描述**：通信方式，mailto是指邮件方式
- **UBL XPath**：`cbc:EndpointID/@schemeID`
- **是否必填**：否

### PartyIdentification.ID
- **描述**：父节点cac:PartyIdentification存在则必填，供应商的标识符
- **UBL XPath**：`cac:PartyIdentification/cbc:ID`
- **是否必填**：父节点存在则必填

### PartyIdentification.ID.schemeID
- **描述**：父节点cac:PartyIdentification存在则必填，
买方标识符的模式标识符
- **UBL XPath**：`cac:PartyIdentification/cbc:ID/@schemeID`
- **是否必填**：父节点存在则必填

### PartyName.Name
- **描述**：买方的名称
- **UBL XPath**：`cac:PartyName/cbc:Name`

### Party.PostalAddress
- **描述**：邮政地址信息
- **UBL XPath**：`cac:Party/cac:PostalAddress`
- **是否必填**：必填

### Postbox
- **描述**：买方的邮政地址信箱
- **UBL XPath**：`cbc:Postbox`
- **是否必填**：否

### StreetName
- **描述**：买方邮件地址的街道名称
- **UBL XPath**：`cbc:StreetName`
- **是否必填**：建议必填

### AdditionalStreetName
- **描述**：买方的邮政地址附加街道名称。用于提供补充主要信息的更多详细信息。
- **UBL XPath**：`cbc:AdditionalStreetName`
- **是否必填**：否

### BuildingNumber
- **描述**：买方的邮政地址建筑号。
- **UBL XPath**：`cbc:BuildingNumber`
- **是否必填**：否

### Department
- **描述**：买方的邮政地址部门。
- **UBL XPath**：`cbc:Department`
- **是否必填**：否

### PlotIdentification
- **描述**：买方邮政地址地块识别。额外的地址号和与此地址相关的地块标识符。
- **UBL XPath**：`cbc:PlotIdentification`
- **是否必填**：否

### CitySubdivisionName
- **描述**：城市内部的行政或区域划分，通常指的是 市区、区域、街区 或其他类似的区域名称
- **UBL XPath**：`cbc:CitySubdivisionName`
- **是否必填**：否

### CityName
- **描述**：买方邮件地址的城市名称
- **UBL XPath**：`cbc:CityName`
- **是否必填**：建议必填

### PostalZone
- **描述**：买方邮件地址的邮政编码
- **UBL XPath**：`cbc:PostalZone`
- **是否必填**：建议必填

### CountrySubentity
- **描述**：一个国家的 次级行政区划，通常指的是 省、州、地区、自治区
- **UBL XPath**：`cbc:CountrySubentity`
- **是否必填**：否

### AddressLine
- **描述**：提供多行地址信息
- **UBL XPath**：`cac:AddressLine`
- **是否必填**：否

### Line
- **描述**：一个具体的地址行内容，例子中：第一行描述的是街道地址 1234 Elm Street，
第二行提供了详细的单元号或公寓信息 Apartment 56B
- **UBL XPath**：`cbc:Line`
- **是否必填**：否

### Country.IdentificationCode
- **描述**：国家/地区的代码，使用来自 ISO3166-1标准的两位字母国家地区代码
- **UBL XPath**：`cac:Country/cbc:IdentificationCode`
- **是否必填**：必填

### Country.Name
- **描述**：国家/地区的名称
- **UBL XPath**：`cac:Country/cbc:Name`
- **是否必填**：否

### PartyTaxScheme
- **描述**：税务信息
- **UBL XPath**：`cac:PartyTaxScheme`
- **是否必填**：必填

### TaxScheme.ID
- **描述**：增值税标识符，使用“VAT”或 "GST"
- **UBL XPath**：`cac:TaxScheme/cbc:ID`
- **是否必填**：必填

### CompanyID
- **描述**：买方的增值税识别号，或为税务目的根据卖方地址定义的本地识别号，
或使卖方能够说明其注册税务状态的参考编号。
- **UBL XPath**：`cbc:CompanyID`
- **是否必填**：必填

### Party.PartyLegalEntity
- **描述**：法律实体相关信息
- **UBL XPath**：`cac:Party/cac:PartyLegalEntity`
- **是否必填**：建议必填

### RegistrationName
- **描述**：买方的正式名称或公司名称
- **UBL XPath**：`cbc:RegistrationName`
- **是否必填**：建议必填

### CompanyID
- **描述**：由官方注册机构颁发的标识符，用于识别买方为合法实体或个人。
为了让买方能够自动识别供应商，必须提供买方标识符、买方法律注册标识符和/或买方增值税标识符。
该字段是可选的，但在大多数情况下应填写。
- **UBL XPath**：`cbc:CompanyID`
- **是否必填**：建议必填

### CompanyID.schemeID
- **描述**：买方的法律注册标识符方案标识符
值必须符合代码列表
- **UBL XPath**：`cbc:CompanyID/@schemeID`
- **是否必填**：建议必填

### CompanyLegalForm
- **描述**：与买方相关的其他法律信息
- **UBL XPath**：`cbc:CompanyLegalForm`
- **是否必填**：否

### Party.Contact
- **描述**：联系方式
- **UBL XPath**：`cac:Party/cac:Contact`
- **是否必填**：建议必填

### Name
- **描述**：联系人名称
- **UBL XPath**：`cbc:Name`
- **是否必填**：建议必填

### Telephone
- **描述**：联系人电话
- **UBL XPath**：`cbc:Telephone`
- **是否必填**：否

### ElectronicMail
- **描述**：联系人电子邮件地址
- **UBL XPath**：`cbc:ElectronicMail`
- **是否必填**：建议必填

### Party.Person
- **描述**：如果买方是个人，则应在特定元素中包含卖方的名字和姓氏。
- **UBL XPath**：`cac:Party/cac:Person`
- **是否必填**：按实际情况必填

### FirstName
- **描述**：个人的名字部分
- **UBL XPath**：`cbc:FirstName`
- **是否必填**：父节点存在则必填

### FamilyName
- **描述**：个人的姓氏
- **UBL XPath**：`cbc:FamilyName`
- **是否必填**：父节点存在则必填

### AccountingContact
- **描述**：会计联系人方式
- **UBL XPath**：`cac:AccountingContact`
- **是否必填**：否

### Name
- **描述**：会计联系人名称
- **UBL XPath**：`cbc:Name`
- **是否必填**：否

### Telephone
- **描述**：会计联系人电话
- **UBL XPath**：`cbc:Telephone`
- **是否必填**：否

### Telefax
- **描述**：会计联系人传值
- **UBL XPath**：`cbc:Telefax`
- **是否必填**：否

### ElectronicMail
- **描述**：会计联系人电子邮件地址
- **UBL XPath**：`cbc:ElectronicMail`
- **是否必填**：否


## 角色信息: 客户
（实际购买方）

### BuyerCustomerParty
- **描述**：仅当买方与会计客户不一致时使用。
如果买方与会计客户一致，使用 cac:AccountingCustomerParty 即可。
- **UBL XPath**：`cac:BuyerCustomerParty`
- **是否必填**：按实际情况必填

### AccountingCustomerParty一样）
- **UBL XPath**：`(和cac:AccountingCustomerParty一样）`


## 角色信息: 税代信息

### TaxRepresentativeParty
- **描述**：税务代理信息
- **UBL XPath**：`cac:TaxRepresentativeParty`
- **是否必填**：按实际情况必填

### Party
- **UBL XPath**：`cac:PartyName`

### PartyName.Name
- **描述**：税务代表主体名称
- **UBL XPath**：`cac:PartyName/cbc:Name`
- **是否必填**：按实际情况必填

### Party.PostalAddress
- **描述**：邮寄地址 (Postal address of party)
- **UBL XPath**：`cac:PostalAddress`
- **是否必填**：否

### StreetName
- **描述**：街道名称 (Name of street)
- **UBL XPath**：`cbc:StreetName`
- **是否必填**：否

### CityName
- **描述**：城市名称 (Name of city)
- **UBL XPath**：`cbc:CityName`
- **是否必填**：否

### PostalZone
- **描述**：邮政编码 (Postal or ZIP code)
- **UBL XPath**：`cbc:PostalZone`
- **是否必填**：否

### AddressLine
- **UBL XPath**：`cac:AddressLine`

### Line
- **描述**：地址信息
- **UBL XPath**：`cbc:Line`
- **是否必填**：建议必填

### Country.IdentificationCode
- **描述**：国家代码 (Country code)
- **UBL XPath**：`cac:Country/cbc:IdentificationCode`
- **是否必填**：按实际情况必填

### PartyTaxScheme
- **UBL XPath**：`cac:PartyTaxScheme`
- **是否必填**：按实际情况必填

### TaxScheme.ID
- **描述**：eg：VAT
- **UBL XPath**：`cac:TaxScheme/cbc:ID`
- **是否必填**：按实际情况必填

### CompanyID
- **描述**：公司ID (Company Tax identification number)
- **UBL XPath**：`cbc:CompanyID`
- **是否必填**：按实际情况必填


## 物流信息：交货信息

### Delivery
- **描述**：交货信息，分批交货可以多次出现
- **UBL XPath**：`cac:Delivery`
- **是否必填**：建议必填
- **示例**：
```xml
<Invoice>
  <!-- Code omitted for clarity -->
  <cac:Delivery>
      <cbc:ActualDeliveryDate>2019-01-01</cbc:ActualDeliveryDate>
      <cbc:LatestDeliveryDate>2019-01-03</cbc:LatestDeliveryDate>
      <cac:DeliveryLocation>
          <cbc:ID schemeID="0088">7300010000001</cbc:ID>
          <cbc:Description>Text describing the delivery location</cbc:Description>
          <cac:Address>
              <cbc:Postbox>121212</cbc:Postbox>
              <cbc:StreetName>Delivery Street</cbc:StreetName>
              <cbc:Department>Delivery Department</cbc:Department>
              <cbc:PlotIdentification>0000</cbc:PlotIdentification>
              <cbc:CitySubdivisionName>Delivery City Subdivision Name</cbc:CitySubdivisionName>
              <cbc:CityName>Delivery City</cbc:CityName>
              <cbc:PostalZone>55555</cbc:PostalZone>
              <cbc:CountrySubentity>Delivery Province</cbc:CountrySubentity>
              <cac:Country>
                  <cbc:IdentificationCode>SE</cbc:IdentificationCode>
                  <cbc:Name>Sweden</cbc:Name>
              </cac:Country>
          </cac:Address>
      </cac:DeliveryLocation>
      <cac:DeliveryParty>
          <cac:PartyName>
              <cbc:Name>Delivery Name</cbc:Name>
          </cac:PartyName>
          <cac:Contact>
              <cbc:Name>Anders Andersson</cbc:Name>
              <cbc:Telephone>01113354</cbc:Telephone>
              <cbc:ElectronicMail>DeliveryContact@mail.com</cbc:ElectronicMail>
          </cac:Contact>
      </cac:DeliveryParty>
      <cac:Despatch>
          <cac:DespatchParty>
              <cac:PartyName>
                  <cbc:Name>Despatch party name</cbc:Name>
              </cac:PartyName>
              <cac:PostalAddress>
                  <cbc:StreetName>Street 1</cbc:StreetName>
                  <cbc:CityName>Jammu</cbc:CityName>
                  <cbc:PostalZone>181131</cbc:PostalZone>
                  <cbc:CountrySubentityCode>01</cbc:CountrySubentityCode>
                  <cac:Country>
                      <cbc:IdentificationCode>IN</cbc:IdentificationCode>
                      <cbc:Name>India</cbc:Name>
                  </cac:Country>
              </cac:PostalAddress>
          </cac:DespatchParty>
      </cac:Despatch>
  </cac:Delivery>
  <!-- Code omitted for clarity -->
</Invoice>
```


### ActualDeliveryDate
- **描述**：货物或服务的实际交付日期，格式：YYYY-MM-DD
- **UBL XPath**：`cbc:ActualDeliveryDate`
- **是否必填**：建议必填

### LatestDeliveryDate
- **描述**：买方允许的最晚交货日期，格式：YYYY-MM-DD
- **UBL XPath**：`cbc:LatestDeliveryDate`
- **是否必填**：否

### DeliveryLocation.ID
- **描述**：交货地点的标识符，例如 GLN 编号
- **UBL XPath**：`cac:DeliveryLocation/cbc:ID`
- **是否必填**：否

### DeliveryLocation.ID.schemeID
- **描述**：交货地点标识符的标识方案
- **UBL XPath**：`cac:DeliveryLocation/cbc:ID/@schemeID`
- **是否必填**：否

### DeliveryLocation.Description
- **描述**：交货地点的描述
- **UBL XPath**：`cac:DeliveryLocation/cbc:Description`
- **是否必填**：否

### DeliveryLocation.Address.Postbox
- **描述**：交货地址的邮政信箱
- **UBL XPath**：`cac:DeliveryLocation/cac:Address/cbc:Postbox`
- **是否必填**：否

### DeliveryLocation.Address.Floor
- **描述**：交货地址的楼层
- **UBL XPath**：`cac:DeliveryLocation/cac:Address/cbc:Floor`
- **是否必填**：否

### DeliveryLocation.Address.Room
- **描述**：交货地址的房间、套间或公寓
- **UBL XPath**：`cac:DeliveryLocation/cac:Address/cbc:Room`
- **是否必填**：否

### DeliveryLocation.Address.StreetName
- **描述**：交货地址的街道名称
- **UBL XPath**：`cac:DeliveryLocation/cac:Address/cbc:StreetName`
- **是否必填**：否

### DeliveryLocation.Address.AdditionalStreetName
- **描述**：交货地址的附加街道名称
- **UBL XPath**：`cac:DeliveryLocation/cac:Address/cbc:AdditionalStreetName`
- **是否必填**：否

### DeliveryLocation.Address.CityName
- **描述**：交货地址的城市名称
- **UBL XPath**：`cac:DeliveryLocation/cac:Address/cbc:CityName`
- **是否必填**：否

### DeliveryLocation.Address.PostalZone
- **描述**：交货地址的邮政编码
- **UBL XPath**：`cac:DeliveryLocation/cac:Address/cbc:PostalZone`
- **是否必填**：否

### DeliveryLocation.Address.Country.IdentificationCode
- **描述**：交货地址的国家代码
- **UBL XPath**：`cac:DeliveryLocation/cac:Address/cac:Country/cbc:IdentificationCode`
- **是否必填**：否

### DeliveryLocation.Country.Name
- **描述**：交货地址的国家名称
- **UBL XPath**：`cac:DeliveryLocation/cac:Country/cbc:Name`
- **是否必填**：否

### CarrierParty.PartyName.Name
- **描述**：承运方的名称
- **UBL XPath**：`cac:CarrierParty/cac:PartyName/cbc:Name`
- **是否必填**：否

### DeliveryParty.PartyName.Name
- **描述**：收货方的名称
- **UBL XPath**：`cac:DeliveryParty/cac:PartyName/cbc:Name`
- **是否必填**：否

### DeliveryParty.Contact.Name
- **描述**：收货方联系人的姓名
- **UBL XPath**：`cac:DeliveryParty/cac:Contact/cbc:Name`
- **是否必填**：否

### DeliveryParty.Contact.Telephone
- **描述**：收货方联系人的电话号码
- **UBL XPath**：`cac:DeliveryParty/cac:Contact/cbc:Telephone`
- **是否必填**：否

### DeliveryParty.Contact.ElectronicMail
- **描述**：收货方联系人的电子邮件
- **UBL XPath**：`cac:DeliveryParty/cac:Contact/cbc:ElectronicMail`
- **是否必填**：否


## 物流信息：交货条款

### DeliveryTerms
- **描述**：交货条款
- **UBL XPath**：`cac:DeliveryTerms`
- **是否必填**：否
- **示例**：
```xml
<cac:DeliveryTerms>
      <cbc:ID>DAP</cbc:ID>
      <cbc:SpecialTerms>Description of the delivery terms</cbc:SpecialTerms>
      <cbc:LossRiskResponsibilityCode>Code to identify the responsibility for the loss risk.</cbc:LossRiskResponsibilityCode>
      <cbc:LossRisk>A description of the responsibility for the loss risk.</cbc:LossRisk>
  </cac:DeliveryTerms>
```


### ID
- **描述**：交货条款代码。
- **UBL XPath**：`cbc:ID`
- **是否必填**：否

### SpecialTerms
- **描述**：交货条款的描述。
- **UBL XPath**：`cbc:SpecialTerms`
- **是否必填**：否

### LossRiskResponsibilityCode
- **描述**：损失风险责任代码。
- **UBL XPath**：`cbc:LossRiskResponsibilityCode`
- **是否必填**：否

### LossRisk
- **描述**：损失风险责任的描述。
- **UBL XPath**：`cbc:LossRisk`
- **是否必填**：否


## 付款：付款方式

### PaymentMeans
- **描述**：付款方式，如果有多种付款方式，可能多次出现
- **UBL XPath**：`cac:PaymentMeans`
- **是否必填**：建议必填
- **示例**：
```xml
<Invoice>
  <!-- Code omitted for clarity -->
  <cac:PaymentMeans>
    <cbc:PaymentMeansCode>30</cbc:PaymentMeansCode>
    <cbc:PaymentID>123456</cbc:PaymentID>
    <cac:PayeeFinancialAccount>
        <cbc:ID>12345678</cbc:ID>
        <cbc:Name>AccountName</cbc:Name>
        <cac:FinancialInstitutionBranch>
            <cbc:ID>SE:BANKGIRO</cbc:ID>
            <cbc:Name>BankName</cbc:Name>
            <cac:Address>
                    <cbc:Postbox>111</cbc:Postbox>
                    <cbc:StreetName>Bank Street</cbc:StreetName>
                    <cbc:BuildingNumber>11</cbc:BuildingNumber>
                    <cbc:Department>Bank Department</cbc:Department>
                    <cbc:PlotIdentification>0000</cbc:PlotIdentification>
                    <cbc:CitySubdivisionName>Bank City Subdivision Name</cbc:CitySubdivisionName>
                    <cbc:CityName>Bank City</cbc:CityName>
                    <cbc:PostalZone>22233</cbc:PostalZone>
                    <cbc:CountrySubentity>Bank Province</cbc:CountrySubentity>
                    <cac:Country>
                        <cbc:IdentificationCode>SE</cbc:IdentificationCode>
                        <cbc:Name>Sweden</cbc:Name>
                    </cac:Country>
                </cac:Address>
        </cac:FinancialInstitutionBranch>
    </cac:PayeeFinancialAccount>
  </cac:PaymentMeans>
  <!-- Code omitted for clarity -->
</Invoice>
```


### PaymentMeansCode
- **描述**：付款方式代码，表示付款将如何结算。
- **UBL XPath**：`cbc:PaymentMeansCode`
- **是否必填**：建议必填

### PaymentMeansCode.name
- **描述**：描述付款方式的名称。
- **UBL XPath**：`cbc:PaymentMeansCode/@name`
- **是否必填**：否

### PaymentID
- **描述**：付款标识符，如 OCR、KID 等。
- **UBL XPath**：`cbc:PaymentID`
- **是否必填**：否

### CardAccount.PrimaryAccountNumberID
- **描述**：用于付款的卡的主要账户号码 (PAN)。发票中不应包含完整的卡主账户号码，以符合卡支付的安全标准。
- **UBL XPath**：`cac:CardAccount/cbc:PrimaryAccountNumberID`
- **是否必填**：否

### CardAccount.NetworkID
- **描述**：卡公司名称。
- **UBL XPath**：`cac:CardAccount/cbc:NetworkID`
- **是否必填**：否

### CardAccount.HolderName
- **描述**：持卡人名称。
- **UBL XPath**：`cac:CardAccount/cbc:HolderName`
- **是否必填**：否

### PayeeFinancialAccount.ID
- **描述**：付款账号，如 IBAN 或 BBAN。
- **UBL XPath**：`cac:PayeeFinancialAccount/cbc:ID`
- **是否必填**：建议必填

### PayeeFinancialAccount.Name
- **描述**：付款账户名称，即付款应汇入的支付服务提供商的账户名称。
- **UBL XPath**：`cac:PayeeFinancialAccount/cbc:Name`
- **是否必填**：建议必填

### PayeeFinancialAccount.CurrencyCode
- **描述**：表示金融账户持有的货币代码，值应符合 ISO 4217 货币代码表。
- **UBL XPath**：`cac:PayeeFinancialAccount/cbc:CurrencyCode`
- **是否必填**：否

### PayeeFinancialAccount.FinancialInstitutionBranch.ID
- **描述**：付款账号标识符，例如 BIC 或 Swift 代码。
- **UBL XPath**：`cac:PayeeFinancialAccount/cac:FinancialInstitutionBranch/cbc:ID`
- **是否必填**：建议必填

### PayeeFinancialAccount.FinancialInstitutionBranch.Name
- **描述**：付款应汇入的银行分支机构或银行部门的名称。
- **UBL XPath**：`cac:PayeeFinancialAccount/cac:FinancialInstitutionBranch/cbc:Name`
- **是否必填**：建议必填

### PayeeFinancialAccount.FinancialInstitutionBranch.Address.Postbox
- **描述**：银行地址的邮政信箱。
- **UBL XPath**：`cac:PayeeFinancialAccount/cac:FinancialInstitutionBranch/cac:Address/cbc:Postbox`
- **是否必填**：否

### PayeeFinancialAccount.FinancialInstitutionBranch.Address.Floor
- **描述**：银行地址的楼层。
- **UBL XPath**：`cac:PayeeFinancialAccount/cac:FinancialInstitutionBranch/cac:Address/cbc:Floor`
- **是否必填**：否

### PayeeFinancialAccount.FinancialInstitutionBranch.Address.Room
- **描述**：银行地址的房间、套房或公寓号。
- **UBL XPath**：`cac:PayeeFinancialAccount/cac:FinancialInstitutionBranch/cac:Address/cbc:Room`
- **是否必填**：否

### PayeeFinancialAccount.FinancialInstitutionBranch.Address.StreetName
- **描述**：银行地址的街道名称。
- **UBL XPath**：`cac:PayeeFinancialAccount/cac:FinancialInstitutionBranch/cac:Address/cbc:StreetName`
- **是否必填**：否

### PayeeFinancialAccount.FinancialInstitutionBranch.Address.CityName
- **描述**：银行地址所在的城市名称。
- **UBL XPath**：`cac:PayeeFinancialAccount/cac:FinancialInstitutionBranch/cac:Address/cbc:CityName`
- **是否必填**：否

### PayeeFinancialAccount.FinancialInstitutionBranch.Address.Country.IdentificationCode
- **描述**：银行地址所在国家的代码。
- **UBL XPath**：`cac:PayeeFinancialAccount/cac:FinancialInstitutionBranch/cac:Address/cac:Country/cbc:IdentificationCode`
- **是否必填**：否

### PaymentMandate.ID
- **描述**：用于引用直接借记付款的付款授权标识符。
- **UBL XPath**：`cac:PaymentMandate/cbc:ID`
- **是否必填**：否

### PaymentMandate.PayerFinancialAccount.ID
- **描述**：用于直接借记付款的付款方账户标识符。
- **UBL XPath**：`cac:PaymentMandate/cac:PayerFinancialAccount/cbc:ID`
- **是否必填**：否


## 付款：付款条件

### PaymentTerms
- **描述**：付款条件
- **UBL XPath**：`cac:PaymentTerms`
- **是否必填**：建议必填

### Note
- **描述**：付款条款描述。
- **UBL XPath**：`cbc:Note`
- **是否必填**：建议必填

### PenaltySurchargePercent
- **描述**：罚款利率，值仅为数值。
- **UBL XPath**：`cbc:PenaltySurchargePercent`
- **是否必填**：否


## 付款：预付款

### PrepaidPayment
- **描述**：预付款信息，可能出现多笔
- **UBL XPath**：`cac:PrepaidPayment`

### PaidAmount
- **描述**：已付款金额，单位为发票货币。
- **UBL XPath**：`cbc:PaidAmount`

### PaidAmount.currencyID
- **描述**：已付款金额的货币，必须与发票货币相同。
- **UBL XPath**：`cbc:PaidAmount/@currencyID`


## 折扣及附加费用

### AllowanceCharge
- **描述**：折扣和附加收费信息，如果存在折扣或者附加费用则必填
- **UBL XPath**：`cac:AllowanceCharge`
- **是否必填**：按实际情况必填
- **示例**：
```xml
<Invoice>
  <!-- Code omitted for clarity -->
  <cac:AllowanceCharge>
    <cbc:ChargeIndicator>false</cbc:ChargeIndicator>
    <cbc:AllowanceChargeReason>Reason for allowance</cbc:AllowanceChargeReason>
    <cbc:Amount currencyID="EUR">5.00</cbc:Amount>
    <cbc:BaseAmount currencyID="EUR">100.00</cbc:BaseAmount>
    <cac:TaxCategory>
        <cbc:ID>Z</cbc:ID>
        <cbc:Percent>0</cbc:Percent>
        <cbc:TaxExemptionReasonCode>vatex-eu-132-1b</cbc:TaxExemptionReasonCode>
        <cbc:TaxExemptionReason>Tax exemption reason description</cbc:TaxExemptionReason>
        <cac:TaxScheme>
            <cbc:ID>VAT</cbc:ID>
        </cac:TaxScheme>
    </cac:TaxCategory>
    <cac:TaxTotal>
        <cbc:TaxAmount currencyID="EUR">0.00</cbc:TaxAmount>
    </cac:TaxTotal>
  </cac:AllowanceCharge>
  <!-- Code omitted for clarity -->
</Invoice>
```


### ChargeIndicator
- **描述**：表示是附加费用（true）还是折扣（false）
- **UBL XPath**：`cbc:ChargeIndicator`
- **是否必填**：必填

### AllowanceChargeReasonCode
- **描述**：折扣或附加费用的原因代码
- **UBL XPath**：`cbc:AllowanceChargeReasonCode`
- **是否必填**：否

### AllowanceChargeReason
- **描述**：折扣或附加费用的原因
- **UBL XPath**：`cbc:AllowanceChargeReason`
- **是否必填**：建议必填

### MultiplierFactorNumeric
- **描述**：折扣或收费的百分比（例如10%应表示为"10"），如果此处有值，cbc:Amount= sum(lineExtensionAmount) * 10%
- **UBL XPath**：`cbc:MultiplierFactorNumeric`
- **是否必填**：建议必填

### Amount
- **描述**：折扣或收费的金额
- **UBL XPath**：`cbc:Amount`
- **是否必填**：必填

### Amount.currencyID
- **描述**：折扣或收费的金额的货币单位
- **UBL XPath**：`cbc:Amount/@currencyID`
- **是否必填**：必填

### BaseAmount
- **描述**：计算折扣或收费金额的基础金额
- **UBL XPath**：`cbc:BaseAmount`
- **是否必填**：否

### BaseAmount.currencyID
- **描述**：折扣或收费金额的基础金额货币
- **UBL XPath**：`cbc:BaseAmount/@currencyID`
- **是否必填**：否

### TaxCategory.ID
- **描述**：折扣或收费的税种代码
- **UBL XPath**：`cac:TaxCategory/cbc:ID`
- **是否必填**：必填

### TaxCategory.Percent
- **描述**：折扣或收费的税率百分比
- **UBL XPath**：`cac:TaxCategory/cbc:Percent`
- **是否必填**：必填

### TaxCategory.TaxExemptionReasonCode
- **描述**：如果折扣或收费免税，则为免税的原因代码
- **UBL XPath**：`cac:TaxCategory/cbc:TaxExemptionReasonCode`

### TaxCategory.TaxExemptionReason
- **描述**：如果折扣或收费免税，则为免税的原因
- **UBL XPath**：`cac:TaxCategory/cbc:TaxExemptionReason`
- **是否必填**：必填

### TaxCategory.TaxScheme.ID
- **描述**：折扣或收费的税种方案标识符
- **UBL XPath**：`cac:TaxCategory/cac:TaxScheme/cbc:ID`
- **是否必填**：必填

### TaxTotal.TaxAmount
- **描述**：折扣或收费的总税额
- **UBL XPath**：`cac:TaxTotal/cbc:TaxAmount`
- **是否必填**：必填

### TaxTotal.TaxAmount.currencyID
- **描述**：折扣或收费的总税额的货币
- **UBL XPath**：`cac:TaxTotal/cbc:TaxAmount/@currencyID`
- **是否必填**：必填


## 税：税收汇率

### TaxExchangeRate
- **描述**：税收汇率，可能出现多个
如果发票或贷记通知单不涉及跨币种的税金计算，则 cac:TaxExchangeRate 是可选的
在贷记通知单中，cac:TaxExchangeRate 应与原发票保持一致，以确保调整金额的准确性和税务合规性。
- **UBL XPath**：`cac:TaxExchangeRate`
- **是否必填**：按实际情况必填
- **示例**：
```xml
<Invoice>
  <cbc:DocumentCurrencyCode>EUR</cbc:DocumentCurrencyCode>
  <cbc:TaxCurrencyCode>USD</cbc:TaxCurrencyCode>
  <!-- Code omitted for clarity -->
  <cac:TaxExchangeRate>
    <cbc:SourceCurrencyCode>EUR</cbc:SourceCurrencyCode>
    <cbc:TargetCurrencyCode>USD</cbc:TargetCurrencyCode>
    <cbc:CalculationRate>1.16</cbc:CalculationRate>
    <cbc:MathematicOperatorCode>Multiply</cbc:MathematicOperatorCode>
    <cbc:Date>2019-01-01</cbc:Date>
  </cac:TaxExchangeRate>
  <!-- Code omitted for clarity -->
</Invoice>
```


### SourceCurrencyCode
- **描述**：源货币代码（文档货币）。值应遵循代码表
- **UBL XPath**：`cbc:SourceCurrencyCode`
- **是否必填**：必填

### TargetCurrencyCode
- **描述**：目标货币代码（税务货币）。值应遵循代码表
- **UBL XPath**：`cbc:TargetCurrencyCode`
- **是否必填**：必填

### CalculationRate
- **描述**：从源货币转换为目标货币使用的汇率。
- **UBL XPath**：`cbc:CalculationRate`
- **是否必填**：建议必传

### MathematicOperatorCode
- **描述**：用于计算税款的数学运算方法，值必须等于“Multiply”。
- **UBL XPath**：`cbc:MathematicOperatorCode`
- **是否必填**：建议必传

### Date
- **描述**：汇率的获取日期，格式为 YYYY-MM-DD。
- **UBL XPath**：`cbc:Date`
- **是否必填**：建议必传


## 税：总税额

### TaxTotal
- **描述**：总税额信息, 涉及多个税种或税区，可以多次出现
- **UBL XPath**：`cac:TaxTotal`
- **是否必填**：必填
- **示例**：
```xml
<Invoice>
  <!-- Code omitted for clarity -->
  <cac:TaxTotal>
    <cbc:TaxAmount currencyID="EUR">25.00</cbc:TaxAmount>
    <cac:TaxSubtotal>
        <cbc:TaxableAmount currencyID="EUR">100.00</cbc:TaxableAmount>
        <cbc:TaxAmount currencyID="EUR">25.00</cbc:TaxAmount>
        <cac:TaxCategory>
            <cbc:ID>S</cbc:ID>
            <cbc:Percent>25</cbc:Percent>
            <cac:TaxScheme>
                <cbc:ID>VAT</cbc:ID>
            </cac:TaxScheme>
        </cac:TaxCategory>
    </cac:TaxSubtotal>
    <cac:TaxSubtotal>
        <cbc:TaxableAmount currencyID="EUR">-5.00</cbc:TaxableAmount>
        <cbc:TaxAmount currencyID="EUR">0.00</cbc:TaxAmount>
        <cac:TaxCategory>
            <cbc:ID>Z</cbc:ID>
            <cbc:Percent>0</cbc:Percent>
            <cac:TaxScheme>
                <cbc:ID>VAT</cbc:ID>
            </cac:TaxScheme>
        </cac:TaxCategory>
    </cac:TaxSubtotal>
  </cac:TaxTotal>
  <!-- Code omitted for clarity -->
</Invoice>
```


### TaxAmount
- **描述**：文档的总税额，以文档货币表示，汇总所有 cac:TaxSubTotal/cbc:TaxAmount。
- **UBL XPath**：`cbc:TaxAmount`
- **是否必填**：必填

### TaxAmount.currencyID
- **描述**：文档总税额的货币代码，必须与 cbc:DocumentCurrencyCode 一致。
- **UBL XPath**：`cbc:TaxAmount/@currencyID`
- **是否必填**：必填

### TaxSubtotal
- **描述**：每个税类的信息，可以多次出现
- **UBL XPath**：`cac:TaxSubtotal`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxableAmount
- **描述**：每个税类的应税总金额
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxableAmount`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxableAmount.currencyID
- **描述**：每个税类的应税总金额货币代码，必须与 cbc:DocumentCurrencyCode 一致。
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxableAmount/@currencyID`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxAmount
- **描述**：每个税类的总税额
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxAmount`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxAmount.currencyID
- **描述**：每个税类的总税额货币代码，必须与 cbc:DocumentCurrencyCode 一致。
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxAmount/@currencyID`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.ID
- **描述**：标识税类的代码，例如 "S"。值应遵循代码表
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:ID`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.Percent
- **描述**：税类的百分比税率。
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:Percent`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.TaxExemptionReasonCode
- **描述**：税类的免税原因代码。仅适用于免税的商品或服务。
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:TaxExemptionReasonCode`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.TaxExemptionReason
- **描述**：免税原因。
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:TaxExemptionReason`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.TaxScheme.ID
- **描述**：税类的税务方案标识符，值应遵循代码表
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cac:TaxScheme/cbc:ID`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.TaxScheme.Name
- **描述**：税类的税务方案名称。可用于指定地方税种类
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cac:TaxScheme/cbc:Name`
- **是否必填**：否


## 税：预扣税

### WithholdingTaxTotal
- **描述**：预扣税
- **UBL XPath**：`cac:WithholdingTaxTotal`
- **是否必填**：否
- **示例**：
```xml
<Invoice>
  <!-- Code omitted for clarity -->
  <cac:WithholdingTaxTotal>
    <cbc:TaxAmount currencyID="EUR">6.00</cbc:TaxAmount>
    <cac:TaxSubtotal>
        <cbc:TaxableAmount currencyID="EUR">100.00</cbc:TaxableAmount>
        <cbc:TaxAmount currencyID="EUR">6.00</cbc:TaxAmount>
        <cac:TaxCategory>
            <cbc:ID>S</cbc:ID>
            <cbc:Percent>6</cbc:Percent>
            <cac:TaxScheme>
                <cbc:ID>INC</cbc:ID>
            </cac:TaxScheme>
        </cac:TaxCategory>
    </cac:TaxSubtotal>
  </cac:WithholdingTaxTotal>
  <!-- Code omitted for clarity -->
</Invoice>
```


### TaxAmount
- **描述**：文档的总税额，以文档货币表示，汇总所有 cac:TaxSubTotal/cbc:TaxAmount。
- **UBL XPath**：`cbc:TaxAmount`
- **是否必填**：父节点存在则必填

### TaxAmount.currencyID
- **描述**：文档总税额的货币代码，必须与 cbc:DocumentCurrencyCode 一致。
- **UBL XPath**：`cbc:TaxAmount/@currencyID`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxableAmount
- **描述**：每个税类的应税总金额。
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxableAmount`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxAmount
- **描述**：每个税类的总税额。
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxAmount`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxCategory.ID
- **描述**：标识税类的代码，例如 "S"。
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:ID`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxCategory.Percent
- **描述**：税类的百分比税率。
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:Percent`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxCategory.TaxScheme.ID
- **描述**：税类的税务方案标识符，值应遵循代码表
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cac:TaxScheme/cbc:ID`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxCategory.TaxScheme.Name
- **描述**：税类的税务方案名称。可用于指定地方税种类
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cac:TaxScheme/cbc:Name`
- **是否必填**：父节点存在则必填

### WithholdingTaxTotal
- **描述**：预扣税信息
- **UBL XPath**：`cac:WithholdingTaxTotal`
- **是否必填**：否
- **示例**：
```xml
<cac:InvoiceLine>
    <!-- Code omitted for clarity -->
    <cac:WithholdingTaxTotal>
      <cbc:TaxAmount currencyID="EUR">6.00</cbc:TaxAmount>
      <cac:TaxSubtotal>
          <cbc:TaxableAmount currencyID="EUR">100.00</cbc:TaxableAmount>
          <cbc:TaxAmount currencyID="EUR">6.00</cbc:TaxAmount>
          <cac:TaxCategory>
              <cbc:ID>S</cbc:ID>
              <cbc:Percent>6</cbc:Percent>
              <cac:TaxScheme>
                  <cbc:ID>INC</cbc:ID>
              </cac:TaxScheme>
          </cac:TaxCategory>
      </cac:TaxSubtotal>
    </cac:cac:WithholdingTaxTotal>
    <!-- Code omitted for clarity -->
  </cac:InvoiceLine>
```


### TaxAmount
- **描述**：总税额，包含所有 TaxSubTotal/TaxAmount 的汇总。
- **UBL XPath**：`cbc:TaxAmount`
- **是否必填**：父节点存在则必填

### TaxAmount.currencyID
- **描述**：总税额的货币，必须与 cbc:DocumentCurrencyCode 相同。
- **UBL XPath**：`cbc:TaxAmount/@currencyID`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxableAmount
- **描述**：每个税率类别的应税总额。
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxableAmount`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxableAmount.currencyID
- **描述**：每个税率类别的应税总额货币，必须与 cbc:DocumentCurrencyCode 相同。
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxableAmount/@currencyID`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxAmount
- **描述**：每个税率类别的总税额。
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxAmount`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxAmount.currencyID
- **描述**：每个税率类别的总税额货币，必须与 cbc:DocumentCurrencyCode 相同。
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxAmount/@currencyID`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxCategory.ID
- **描述**：税类代码，例如 "S"。
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:ID`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxCategory.Percent
- **描述**：税类的百分比税率。
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:Percent`
- **是否必填**：父节点存在则必填

### TaxSubtotal.TaxCategory.TaxExemptionReasonCode
- **描述**：税豁免代码，适用于免税的商品或服务。
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:TaxExemptionReasonCode`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.TaxExemptionReason
- **描述**：税豁免原因，适用于免税的商品或服务。
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:TaxExemptionReason`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.TaxScheme.ID
- **描述**：税方案标识符，参考代码表
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cac:TaxScheme/cbc:ID`
- **是否必填**：父节点存在则必填


## 发票上法律
要求的总金额信息

### LegalMonetaryTotal
- **描述**：发票上法律要求的总金额信息
- **UBL XPath**：`cac:LegalMonetaryTotal`
- **是否必填**：必填
- **示例**：
```xml
<Invoice>
  <!-- Code omitted for clarity -->
  <cac:LegalMonetaryTotal>
        <cbc:LineExtensionAmount currencyID="EUR">100.00</cbc:LineExtensionAmount>
        <cbc:TaxExclusiveAmount currencyID="EUR">95.00</cbc:TaxExclusiveAmount>
        <cbc:TaxInclusiveAmount currencyID="EUR">120.00</cbc:TaxInclusiveAmount>
        <cbc:AllowanceTotalAmount currencyID="EUR">5.00</cbc:AllowanceTotalAmount>
        <cbc:ChargeTotalAmount currencyID="EUR">0.00</cbc:ChargeTotalAmount>
        <cbc:PayableAmount currencyID="EUR">110.00</cbc:PayableAmount>
  </cac:LegalMonetaryTotal>
  <!-- Code omitted for clarity -->
</Invoice>
```


### LineExtensionAmount
- **描述**：所有行项目净金额的汇总
- **UBL XPath**：`cbc:LineExtensionAmount`
- **是否必填**：必填

### LineExtensionAmount.currencyID
- **描述**：所有行项目净金额的货币，必须与 cbc:DocumentCurrencyCode 相同
- **UBL XPath**：`cbc:LineExtensionAmount/@currencyID`
- **是否必填**：必填

### TaxExclusiveAmount
- **描述**：发票的不含税总金额
- **UBL XPath**：`cbc:TaxExclusiveAmount`
- **是否必填**：必填

### TaxExclusiveAmount.currencyID
- **描述**：发票不含税总金额的货币，必须与 cbc:DocumentCurrencyCode 相同
- **UBL XPath**：`cbc:TaxExclusiveAmount/@currencyID`
- **是否必填**：必填

### TaxInclusiveAmount
- **描述**：发票含税总金额
- **UBL XPath**：`cbc:TaxInclusiveAmount`
- **是否必填**：必填

### TaxInclusiveAmount.currencyID
- **描述**：发票含税总金额的货币，必须与 cbc:DocumentCurrencyCode 相同
- **UBL XPath**：`cbc:TaxInclusiveAmount/@currencyID`
- **是否必填**：必填

### AllowanceTotalAmount
- **描述**：发票所有折扣金额的汇总（当 cbc:ChargeIndicator 为 false 时计算）
- **UBL XPath**：`cbc:AllowanceTotalAmount`
- **是否必填**：必填

### AllowanceTotalAmount.currencyID
- **描述**：折扣金额的货币，必须与 cbc:DocumentCurrencyCode 相同
- **UBL XPath**：`cbc:AllowanceTotalAmount/@currencyID`
- **是否必填**：必填

### ChargeTotalAmount
- **描述**：发票所有附加费金额的汇总（当 cbc:ChargeIndicator 为 true 时计算，为false时传0.00）
- **UBL XPath**：`cbc:ChargeTotalAmount`
- **是否必填**：按实际情况必填

### ChargeTotalAmount.currencyID
- **描述**：附加费金额的货币，必须与 cbc:DocumentCurrencyCode 相同
- **UBL XPath**：`cbc:ChargeTotalAmount/@currencyID`
- **是否必填**：按实际情况必填

### PrepaidAmount
- **描述**：已预付金额，应从应付金额中扣除, 没有预付款则传0.00
- **UBL XPath**：`cbc:PrepaidAmount`
- **是否必填**：按实际情况必填

### PrepaidAmount.currencyID
- **描述**：预付款金额的货币，必须与 cbc:DocumentCurrencyCode 相同
- **UBL XPath**：`cbc:PrepaidAmount/@currencyID`
- **是否必填**：按实际情况必填

### PayableRoundingAmount
- **描述**：四舍五入金额，应用于应付金额的计算
- **UBL XPath**：`cbc:PayableRoundingAmount`
- **是否必填**：按实际情况必填

### PayableRoundingAmount.currencyID
- **描述**：四舍五入金额的货币，必须与 cbc:DocumentCurrencyCode 相同
- **UBL XPath**：`cbc:PayableRoundingAmount/@currencyID`
- **是否必填**：按实际情况必填

### PayableAmount
- **描述**：应付总金额，包括所有折扣和四舍五入后的结果
- **UBL XPath**：`cbc:PayableAmount`
- **是否必填**：必填

### PayableAmount.currencyID
- **描述**：应付金额的货币，必须与 cbc:DocumentCurrencyCode 相同
- **UBL XPath**：`cbc:PayableAmount/@currencyID`
- **是否必填**：必填

### InvoiceLine
- **描述**：顶级节点
- **UBL XPath**：`cac:InvoiceLine`
- **是否必填**：必填

### ID
- **描述**：行号
- **UBL XPath**：`cbc:ID`
- **是否必填**：必填
- **示例**：
```xml
<Invoice>
  <!-- Code omitted for clarity -->
  <cac:InvoiceLine>
    <cbc:ID>1</cbc:ID>
    <!-- Code omitted for clarity -->
  </cac:InvoiceLine>
  <!-- Code omitted for clarity -->
</Invoice>
```


### Note
- **描述**：备注，可多次重复，表示自由文本。
- **UBL XPath**：`cbc:Note`
- **是否必填**：否
- **示例**：
```xml
<Invoice>
  <!-- Code omitted for clarity -->
  <cac:InvoiceLine>
    <!-- Code omitted for clarity -->
    <cbc:Note>This</cbc:Note>
    <cbc:Note>is an</cbc:Note>
    <cbc:Note>Example</cbc:Note>
    <!-- Code omitted for clarity -->
  </cac:InvoiceLine>
  <!-- Code omitted for clarity -->
</Invoice>
```


### InvoicedQuantity
- **描述**：发票行项目的数量,
 如果是credit note，这里的path节点为cbc:CreditedQuantity
- **UBL XPath**：`cbc:InvoicedQuantity`
- **是否必填**：必填
- **示例**：
```xml
<cac:InvoiceLine>
    <cbc:InvoicedQuantity unitCode="EA">1</cbc:InvoicedQuantity>
  </cac:InvoiceLine>
```


### InvoicedQuantity.unitCode
- **描述**：发票行数量的单位，
如果是credit note，这里的path节点为cbc:CreditedQuantity/@unitCode
- **UBL XPath**：`cbc:InvoicedQuantity/@unitCode`
- **是否必填**：必填

### LineExtensionAmount
- **描述**：发票行的净金额，考虑了数量和可能的折扣/附加费
- **UBL XPath**：`cbc:LineExtensionAmount`
- **是否必填**：必填
- **示例**：
```xml
<cac:InvoiceLine>
    <cbc:LineExtensionAmount currencyID="EUR">100.00</cbc:LineExtensionAmount>
  </cac:InvoiceLine>
```


### LineExtensionAmount.currencyID
- **描述**：使用的货币，必须与 cbc:DocumentCurrencyCode 一致
- **UBL XPath**：`cbc:LineExtensionAmount/@currencyID`
- **是否必填**：必填

### AccountingCost
- **描述**：发票行的会计参考信息。买方可以使用该字段来将发票中的
某个行项目与其内部的会计科目、成本中心、项目代码等匹配。
这有助于在财务系统中进行正确的分类和记账。
- **UBL XPath**：`cbc:AccountingCost`
- **是否必填**：否
- **示例**：
```xml
<cac:InvoiceLine>
    <cbc:AccountingCost>Accounting cost reference</cbc:AccountingCost>
  </cac:InvoiceLine>
```


### InvoicePeriod
- **描述**：发票期间信息
- **UBL XPath**：`cac:InvoicePeriod`
- **是否必填**：否
- **示例**：
```xml
<cac:InvoiceLine>
    <!-- Code omitted for clarity -->
    <cac:InvoicePeriod>
      <cbc:StartDate>2021-01-01</cbc:StartDate>
      <cbc:EndDate>2021-01-31</cbc:EndDate>
    </cac:InvoicePeriod>
    <!-- Code omitted for clarity -->
  </cac:InvoiceLine>
```


### StartDate
- **描述**：发票行的开始日期，格式为 YYYY-MM-DD
- **UBL XPath**：`cbc:StartDate`
- **是否必填**：父节点存在则必填

### EndDate
- **描述**：发票行的结束日期，格式为 YYYY-MM-DD
- **UBL XPath**：`cbc:EndDate`
- **是否必填**：父节点存在则必填


## 行基础数据：
开票项信息

### Item
- **描述**：描述发票行中的物品或服务的详细信息
- **UBL XPath**：`cac:Item`
- **是否必填**：必填
- **示例**：
```xml
<cac:InvoiceLine>
    <!-- Code omitted for clarity -->
    <cac:Item>
      <cbc:Description>Item description</cbc:Description>
      <cbc:Name>Item name</cbc:Name>
      <cac:BuyersItemIdentification>
          <cbc:ID>BuyersItemIdentification</cbc:ID>
      </cac:BuyersItemIdentification>
      <cac:SellersItemIdentification>
          <cbc:ID>SellersItemIdentification</cbc:ID>
      </cac:SellersItemIdentification>
      <cac:ManufacturersItemIdentification>
          <cbc:ID>ManufacturersItemIdentification</cbc:ID>
      </cac:ManufacturersItemIdentification>
      <cac:StandardItemIdentification>
          <cbc:ID schemeID="0088">7300010000001</cbc:ID>
      </cac:StandardItemIdentification>
      <cac:ClassifiedTaxCategory>
          <cbc:ID schemeID="UNCL5305">S</cbc:ID>
          <cbc:Percent>25</cbc:Percent>
          <cac:TaxScheme>
              <cbc:ID>VAT</cbc:ID>
          </cac:TaxScheme>
      </cac:ClassifiedTaxCategory>
      <cac:AdditionalItemProperty>
        <cbc:Name>Size</cbc:Name>
        <cbc:Value>XXL</cbc:Value>
      </cac:AdditionalItemProperty>
      <cac:ItemInstance>
          <cbc:ManufactureDate>2018-01-01</cbc:ManufactureDate>
          <cbc:BestBeforeDate>2018-01-01</cbc:BestBeforeDate>
          <cbc:SerialID>123456789</cbc:SerialID>
          <cac:LotIdentification>
              <cbc:LotNumberID>1111111</cbc:LotNumberID>
          </cac:LotIdentification>
      </cac:ItemInstance>
    </cac:Item>
      <!-- Code omitted for clarity -->
  </cac:InvoiceLine>
```


### Description
- **描述**：物品的描述。
- **UBL XPath**：`cbc:Description`
- **是否必填**：建议传入

### Name
- **描述**：物品的名称。
- **UBL XPath**：`cbc:Name`
- **是否必填**：必填

### BuyersItemIdentification
- **描述**：买方为物品分配的信息
- **UBL XPath**：`cac:BuyersItemIdentification`
- **是否必填**：否

### BuyersItemIdentification.ID
- **描述**：买方为物品分配的标识符
- **UBL XPath**：`cac:BuyersItemIdentification/cbc:ID`
- **是否必填**：父节点存在则必填

### SellersItemIdentification
- **描述**：卖方为物品分配的信息
- **UBL XPath**：`cac:SellersItemIdentification`
- **是否必填**：否

### SellersItemIdentification.ID
- **描述**：卖方为物品分配的标识符
- **UBL XPath**：`cac:SellersItemIdentification/cbc:ID`
- **是否必填**：父节点存在则必填

### ManufacturersItemIdentification
- **描述**：制造商为物品分配的信息
- **UBL XPath**：`cac:ManufacturersItemIdentification`
- **是否必填**：否

### ManufacturersItemIdentification.ID
- **描述**：制造商为物品分配的标识符
- **UBL XPath**：`cac:ManufacturersItemIdentification/cbc:ID`
- **是否必填**：父节点存在则必填

### StandardItemIdentification
- **描述**：基于官方注册的物品信息
- **UBL XPath**：`cac:StandardItemIdentification`
- **是否必填**：否

### StandardItemIdentification.ID
- **描述**：基于官方注册的物品标识符
- **UBL XPath**：`cac:StandardItemIdentification/cbc:ID`
- **是否必填**：父节点存在则必填

### StandardItemIdentification.ID.schemeID
- **描述**：标准物品注册的方案标识符
- **UBL XPath**：`cac:StandardItemIdentification/cbc:ID/@schemeID`
- **是否必填**：父节点存在则必填

### OriginCountry
- **描述**：物品的原产国信息
- **UBL XPath**：`cac:OriginCountry`
- **是否必填**：否

### OriginCountry.IdentificationCode
- **描述**：物品的原产国代码
- **UBL XPath**：`cac:OriginCountry/cbc:IdentificationCode`
- **是否必填**：否

### CommodityClassification
- **描述**：物品的分类信息
- **UBL XPath**：`cac:CommodityClassification`
- **是否必填**：否

### CommodityClassification.ItemClassificationCode
- **描述**：物品的分类代码。
- **UBL XPath**：`cac:CommodityClassification/cbc:ItemClassificationCode`
- **是否必填**：否

### CommodityClassification.ItemClassificationCode.listID
- **描述**：分类代码的方案标识符。
- **UBL XPath**：`cac:CommodityClassification/cbc:ItemClassificationCode/@listID`
- **是否必填**：否

### CommodityClassification.ItemClassificationCode.listVersionID
- **描述**：分类代码方案版本标识符。
- **UBL XPath**：`cac:CommodityClassification/cbc:ItemClassificationCode/@listVersionID`
- **是否必填**：否

### ClassifiedTaxCategory
- **描述**：税类信息
- **UBL XPath**：`cac:ClassifiedTaxCategory`
- **是否必填**：必填

### ClassifiedTaxCategory.ID
- **描述**：税类代码，例如 "S"。
- **UBL XPath**：`cac:ClassifiedTaxCategory/cbc:ID`
- **是否必填**：必填

### ClassifiedTaxCategory.ID.schemeID
- **描述**：编码体系,UNCL5305 是联合国/贸易数据元代码表 
(UN/ECE Recommendation 20) 的代码集，专门用于定义税务类别。
- **UBL XPath**：`cac:ClassifiedTaxCategory/cbc:ID/@schemeID`
- **是否必填**：必填

### ClassifiedTaxCategory.Percent
- **描述**：税类的百分比税率。
- **UBL XPath**：`cac:ClassifiedTaxCategory/cbc:Percent`
- **是否必填**：必填

### ClassifiedTaxCategory.TaxScheme.ID
- **描述**：税方案标识符，参考代码表
- **UBL XPath**：`cac:ClassifiedTaxCategory/cac:TaxScheme/cbc:ID`
- **是否必填**：必填

### AdditionalItemProperty
- **描述**：物品属性的信息
- **UBL XPath**：`cac:AdditionalItemProperty`
- **是否必填**：否

### AdditionalItemProperty.Name
- **描述**：物品属性的名称
- **UBL XPath**：`cac:AdditionalItemProperty/cbc:Name`
- **是否必填**：父节点存在则必填

### AdditionalItemProperty.Value
- **描述**：物品属性的值
- **UBL XPath**：`cac:AdditionalItemProperty/cbc:Value`
- **是否必填**：否

### ItemInstance
- **描述**：物品实例的详细信息
- **UBL XPath**：`cac:ItemInstance`
- **是否必填**：特定商品必填

### ItemInstance.ManufactureDate
- **描述**：物品的生产日期
- **UBL XPath**：`cac:ItemInstance/cbc:ManufactureDate`
- **是否必填**：特定商品必填

### ItemInstance.BestBeforeDate
- **描述**：物品的最佳使用日期
- **UBL XPath**：`cac:ItemInstance/cbc:BestBeforeDate`
- **是否必填**：特定商品必填

### ItemInstance.SerialID
- **描述**：物品的序列号
- **UBL XPath**：`cac:ItemInstance/cbc:SerialID`
- **是否必填**：特定商品必填

### ItemInstance.LotIdentification.LotNumberID
- **描述**：物品的批号标识符
- **UBL XPath**：`cac:ItemInstance/cac:LotIdentification/cbc:LotNumberID`
- **是否必填**：特定商品必填

### ItemInstance.LotIdentification.ExpiryDate
- **描述**：批号的过期日期
- **UBL XPath**：`cac:ItemInstance/cac:LotIdentification/cbc:ExpiryDate`
- **是否必填**：特定商品必填


## 行基础数据：价格

### Price
- **描述**：发票行中的价格信息
- **UBL XPath**：`cac:Price`
- **是否必填**：必填
- **示例**：
```xml
<cac:InvoiceLine>
    <!-- Code omitted for clarity -->
    <cac:Price>
      <cbc:PriceAmount currencyID="EUR">100.00</cbc:PriceAmount>
      <cbc:BaseQuantity unitCode="EA">1</cbc:BaseQuantity>
      <cac:AllowanceCharge>
        <cbc:ChargeIndicator>false</cbc:ChargeIndicator>
        <cbc:Amount currencyID="EUR">10</cbc:Amount>
        <cbc:BaseAmount currencyID="EUR">110.00</cbc:BaseAmount>
      </cac:AllowanceCharge>
    </cac:Price>
    <!-- Code omitted for clarity -->
  </cac:InvoiceLine>
```


### PriceAmount
- **描述**：物品的单价，此值不得为负。
- **UBL XPath**：`cbc:PriceAmount`
- **是否必填**：必填

### PriceAmount.currencyID
- **描述**：cbc:PriceAmount 的货币类型，必须与 cbc:DocumentCurrencyCode 相同。
- **UBL XPath**：`cbc:PriceAmount/@currencyID`
- **是否必填**：必填

### BaseQuantity
- **描述**：适用该价格的商品单位数量
- **UBL XPath**：`cbc:BaseQuantity`
- **是否必填**：否

### BaseQuantity.unitCode
- **描述**：基本数量的计量单位。必须与开票/贷项数量的单位代码相同。
- **UBL XPath**：`cbc:BaseQuantity/@unitCode`
- **是否必填**：父节点存在则必填

### AllowanceCharge
- **描述**：单价（价格）相关的折扣或附加费用
- **UBL XPath**：`cac:AllowanceCharge`
- **是否必填**：按实际情况必填

### AllowanceCharge.ChargeIndicator
- **描述**：对于 cac:Price 部分，仅允许使用折扣，此值必须为 "false"
- **UBL XPath**：`cac:AllowanceCharge/cbc:ChargeIndicator`
- **是否必填**：父节点存在则必填

### AllowanceCharge.Amount
- **描述**：应用到价格上的折让金额，此值仅供参考，折让金额应已在 cbc:PriceAmount 中扣除。
- **UBL XPath**：`cac:AllowanceCharge/cbc:Amount`
- **是否必填**：父节点存在则必填

### AllowanceCharge.Amount.currencyID
- **描述**：cbc:Amount 的货币类型，必须与 cbc:DocumentCurrencyCode 相同。
- **UBL XPath**：`cac:AllowanceCharge/cbc:Amount/@currencyID`
- **是否必填**：父节点存在则必填

### AllowanceCharge.BaseAmount
- **描述**：物品的基础价格，在应用任何折让之前，此值不得为负。
- **UBL XPath**：`cac:AllowanceCharge/cbc:BaseAmount`
- **是否必填**：父节点存在则必填

### AllowanceCharge.BaseAmount.currencyID
- **描述**：cbc:BaseAmount 的货币类型，必须与 cbc:DocumentCurrencyCode 相同。
- **UBL XPath**：`cac:AllowanceCharge/cbc:BaseAmount/@currencyID`
- **是否必填**：父节点存在则必填


## 行基础数据：
折扣或附加费

### AllowanceCharge
- **描述**：折扣及附加费用信息
- **UBL XPath**：`cac:AllowanceCharge`
- **是否必填**：按实际情况必填
- **示例**：
```xml
<cac:InvoiceLine>
    <!-- Code omitted for clarity -->
    <cac:AllowanceCharge>
      <cbc:ChargeIndicator>false</cbc:ChargeIndicator>
      <cbc:AllowanceChargeReason>Reason for allowance</cbc:AllowanceChargeReason>
      <cbc:MultiplierFactorNumeric>5</cbc:MultiplierFactorNumeric>
      <cbc:Amount currencyID="EUR">5.00</cbc:Amount>
      <cbc:BaseAmount currencyID="EUR">100.00</cbc:BaseAmount>
    </cac:AllowanceCharge>
    <!-- Code omitted for clarity -->
  </cac:InvoiceLine>
```


### ChargeIndicator
- **描述**：指示是否为费用 (true) 或折扣 (false)。
- **UBL XPath**：`cbc:ChargeIndicator`
- **是否必填**：父节点存在则必填

### AllowanceChargeReasonCode
- **描述**：费用或折扣原因代码，建议参考代码表
- **UBL XPath**：`cbc:AllowanceChargeReasonCode`
- **是否必填**：建议传入

### AllowanceChargeReason
- **描述**：费用或折扣原因的描述。
- **UBL XPath**：`cbc:AllowanceChargeReason`
- **是否必填**：父节点存在则必填

### MultiplierFactorNumeric
- **描述**：费用或折扣百分比（例如 10% 表示为 "10"）。
- **UBL XPath**：`cbc:MultiplierFactorNumeric`
- **是否必填**：父节点存在则必填

### Amount
- **描述**：费用或折扣金额。
- **UBL XPath**：`cbc:Amount`
- **是否必填**：父节点存在则必填

### Amount.currencyID
- **描述**：费用或折扣金额的货币代码，参考代码表
- **UBL XPath**：`cbc:Amount/@currencyID`
- **是否必填**：父节点存在则必填

### BaseAmount
- **描述**：计算费用或折扣的基准金额。
- **UBL XPath**：`cbc:BaseAmount`
- **是否必填**：否

### BaseAmount.currencyID
- **描述**：基准金额的货币代码，参考参考代码表
- **UBL XPath**：`cbc:BaseAmount/@currencyID`
- **是否必填**：否


## 税

### TaxTotal
- **描述**：行级总税额。如果在发票中的某一行项目上有多个税种
（即同一商品或服务需要征收不同种类的税），那么对于每一个税种，
必须在该行的 cac:InvoiceLine/cac:TaxTotal/cac:TaxSubtotal 中提供详细的税额信息
- **UBL XPath**：`cac:TaxTotal`
- **是否必填**：必填
- **示例**：
```xml
<cac:InvoiceLine>
    <!-- Code omitted for clarity -->
    <cac:TaxTotal>
      <cbc:TaxAmount currencyID="EUR">25.00</cbc:TaxAmount>
      <cac:TaxSubtotal>
          <cbc:TaxableAmount currencyID="EUR">100.00</cbc:TaxableAmount>
          <cbc:TaxAmount currencyID="EUR">25.00</cbc:TaxAmount>
          <cac:TaxCategory>
              <cbc:ID>S</cbc:ID>
              <cbc:Percent>25</cbc:Percent>
              <cac:TaxScheme>
                  <cbc:ID>VAT</cbc:ID>
              </cac:TaxScheme>
          </cac:TaxCategory>
      </cac:TaxSubtotal>
      <cac:TaxSubtotal>
          <cbc:TaxableAmount currencyID="EUR">-5.00</cbc:TaxableAmount>
          <cbc:TaxAmount currencyID="EUR">0.00</cbc:TaxAmount>
          <cac:TaxCategory>
              <cbc:ID>Z</cbc:ID>
              <cbc:Percent>0</cbc:Percent>
              <cac:TaxScheme>
                  <cbc:ID>VAT</cbc:ID>
              </cac:TaxScheme>
          </cac:TaxCategory>
      </cac:TaxSubtotal>
    </cac:TaxTotal>
```


### TaxAmount
- **描述**：总税额，包含所有 TaxSubTotal/TaxAmount 的汇总。
- **UBL XPath**：`cbc:TaxAmount`
- **是否必填**：必填

### TaxAmount.currencyID
- **描述**：总税额货币，必须与 cbc:DocumentCurrencyCode 相同。
- **UBL XPath**：`cbc:TaxAmount/@currencyID`
- **是否必填**：必填

### TaxSubtotal
- **描述**：每个税率类别信息
- **UBL XPath**：`cac:TaxSubtotal`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxableAmount
- **描述**：每个税率类别的应税总额。
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxableAmount`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxableAmount.currencyID
- **描述**：每个税率类别的应税总额货币，必须与 cbc:DocumentCurrencyCode 相同。
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxableAmount/@currencyID`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxAmount
- **描述**：每个税率类别的总税额。
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxAmount`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxAmount.currencyID
- **描述**：每个税率类别的总税额货币，必须与 cbc:DocumentCurrencyCode 相同。
- **UBL XPath**：`cac:TaxSubtotal/cbc:TaxAmount/@currencyID`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.ID
- **描述**：税类代码，例如 "S"。
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:ID`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.Percent
- **描述**：税类的百分比税率，如25%税率填写“25”
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:Percent`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.TaxExemptionReasonCode
- **描述**：税豁免代码，适用于免税的商品或服务。
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:TaxExemptionReasonCode`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.TaxExemptionReason
- **描述**：税豁免原因，适用于免税的商品或服务。
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cbc:TaxExemptionReason`
- **是否必填**：按实际情况必填

### TaxSubtotal.TaxCategory.TaxScheme.ID
- **描述**：税方案标识符，参考代码表
- **UBL XPath**：`cac:TaxSubtotal/cac:TaxCategory/cac:TaxScheme/cbc:ID`
- **是否必填**：按实际情况必填


## 附件

### DocumentReference
- **描述**：与本发票行相关的引用文档，比如采购单、合同、其他发票等
- **UBL XPath**：`cac:DocumentReference`
- **是否必填**：否
- **示例**：
```xml
<cac:InvoiceLine>
    <!-- Code omitted for clarity -->
    <cac:DocumentReference>
      <cbc:ID schemeID="AIT">1145</cbc:ID>
      <cbc:DocumentTypeCode>130</cbc:DocumentTypeCode>
    </cac:DocumentReference>
    <!-- Code omitted for clarity -->
  </cac:InvoiceLine>
```


### ID
- **描述**：引用对象的标识符。
- **UBL XPath**：`cbc:ID`
- **是否必填**：父节点存在则必填

### ID.schemeID
- **描述**：引用对象的方案标识符，参考代码表
- **UBL XPath**：`cbc:ID/@schemeID`
- **是否必填**：父节点存在则必填

### IssueDate
- **描述**：引用文件的发行日期，格式为 YYYY-MM-DD。
- **UBL XPath**：`cbc:IssueDate`
- **是否必填**：否

### IssueTime
- **描述**：引用文件的发行时间，格式为 HH:mm:ss, HH:mm:ssZZZZ等。
- **UBL XPath**：`cbc:IssueTime`
- **是否必填**：否

### DocumentTypeCode
- **描述**：文件类型代码，如果引用的是开票对象，文件类型代码应为 "130"。
- **UBL XPath**：`cbc:DocumentTypeCode`
- **是否必填**：否
