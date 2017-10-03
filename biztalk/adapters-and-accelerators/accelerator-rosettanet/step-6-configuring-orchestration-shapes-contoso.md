---
title: "Étape 6 : Configuration des formes d’Orchestration (Contoso) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, configuring shapes
- private process tutorial, configuring orchestration shapes
ms.assetid: ce680693-cf72-4ca6-a062-019de5a9257b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4185ea50d86b30df4bb61161bf6927845aff5c09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-configuring-orchestration-shapes-contoso"></a>Étape 6 : Configuration des formes d’Orchestration (Contoso)
Dans cette étape, vous configurez les formes orchestration que vous avez ajouté à l’orchestration PrivateResponder que vous avez créé dans [étape 5 : modification de l’Orchestration de processus privé Contoso](../../adapters-and-accelerators/accelerator-rosettanet/step-5-modifying-the-contoso-private-process-orchestration.md). Cela inclut la configuration de la communication entre [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] et le système de planification ERP (Enterprise Resource) pour Contoso.  
  
### <a name="to-configure-the-constructmessagepip3a2requestmessage-shape"></a>Pour configurer la forme ConstructMessagePIP3A2RequestMessage  
  
1.  Sélectionnez PrivateResponder.odx dans l'Explorateur de solutions, puis sur l'aire de conception de l'orchestration, sélectionnez la forme **ConstructPIP3A2RequestMessage** .  
  
2.  Dans la fenêtre Propriétés, sélectionnez la propriété **Messages construits** , sélectionnez **PIP3A2RequestMessage** dans la liste déroulante, puis appuyez sur **Entrée**.  
  
3.  Double-cliquez sur la forme **Assignation du message** dans la forme **ConstructPIP3A2RequestMessage** pour ouvrir l'Éditeur d'expression BizTalk.  
  
4.  Dans l'Éditeur d'expression BizTalk, tapez ce qui suit :  
  
    ```  
    PIP3A2RequestMessage = Helper.NormalizeHeader(Microsoft.Solutions.BTARN.Shared.SCContainer.ConvertFromContainer(ActionMessage));  
    ```  
  
5.  Cliquez sur **OK**.  
  
### <a name="to-configure-the-constructcontoso3a2requestmessage-transform-shape"></a>Pour configurer la forme Transformer ConstructContoso3A2RequestMessage  
  
1.  Sur l'aire de conception de l'orchestration, cliquez sur la forme **ConstructContoso3A2RequestMessage** .  
  
2.  Dans la fenêtre Propriétés, sélectionnez la propriété **Messages construits** , puis sélectionnez **Contoso3A2RequestMessage** dans la liste déroulante.  
  
3.  Sélectionnez la forme **Transform_1** dans la forme **ConstructContoso3A2RequestMessage** .  
  
4.  Dans la fenêtre Propriétés, sélectionnez la propriété **Nom de mappage** , puis cliquez sur le bouton de sélection (**…**) pour ouvrir la boîte de dialogue Configuration de la forme Transformer.  
  
5.  Dans la boîte de dialogue, cliquez sur **mappage existant**, puis, dans le **zone de nom de mappage complet**, sélectionnez  **\<sélectionner dans l’Assembly référencé >** dans la liste déroulante pour ouvrir la boîte de dialogue Sélectionner le Type d’artefact.  
  
6.  Dans la boîte de dialogue Sélectionner le type d'artefact, sélectionnez l'assembly **ContosoPriceAndAvailability** dans le volet gauche, sélectionnez le mappage **PIP3A2RequestToContosoPriceRequest** dans le volet droit, puis cliquez sur **OK**.  
  
7.  Dans la boîte de dialogue Configuration de la forme Transformer, sélectionnez **Source** dans le volet gauche.  
  
8.  Cliquez sur la zone vide sous **Nom de la variable**, puis sélectionnez **PIP3A2RequestMessage** dans la liste déroulante.  
  
9. Sélectionnez **Destination** dans le volet gauche, cliquez sur **Contoso3A2RequestMessage** à partir de la **VariableName** liste déroulante, puis cliquez sur **OK**.  
  
### <a name="to-configure-the-execute3a2vocabulary-call-rules-shape"></a>Pour configurer la forme de règles d'appel Execute3A2Vocabulary  
  
1.  Sur l'aire de conception de l'orchestration, double-cliquez sur la forme **Execute3A2Vocabulary** dans la forme **Scope_1** .  
  
2.  Dans la boîte de dialogue Configuration de la stratégie RèglesAppel, sélectionnez **3A2PriceAvailabilityPolicy** dans la liste déroulante **Sélectionnez la stratégie commerciale que vous souhaitez appeler** .  
  
3.  Dans la liste **Spécifiez les paramètres de stratégie** , cliquez sur **Cliquez ici pour ajouter une nouvelle ligne**, puis sélectionnez **Contoso3A2ResponseMessage** dans la liste déroulante.  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-configure-the-construct3a2responsemessage-transform-shape"></a>Pour configurer la forme Transformer Construct3A2ResponseMessage  
  
1.  Sur l'aire de conception de l'orchestration, cliquez sur la forme **Construct3A2ResponseMessage** .  
  
2.  Dans la fenêtre Propriétés, sélectionnez la propriété **Messages construits** , sélectionnez **PIP3A2ResponseMessage** dans la liste déroulante, puis appuyez sur **Entrée**.  
  
3.  Sélectionnez la forme **Transform_2** dans la forme **Construct3A2ResponseMessage** .  
  
4.  Dans la fenêtre Propriétés, cliquez sur **Nom de mappage**, puis cliquez sur le bouton de sélection (**...**).  
  
5.  Dans la boîte de dialogue Configuration de la forme Transformer, cliquez sur **Nouveau mappage**.  
  
6.  Dans la zone **Nom de mappage complet** , tapez **ContosoPriceAndAvailability.ContosoResponse3A2RequestMerge**.  
  
7.  Dans la boîte de dialogue Configuration de la forme Transformer, sélectionnez **Source** dans le volet gauche.  
  
8.  Cliquez sur l'étiquette **Cliquez ici pour ajouter une nouvelle ligne** sous **Nom de la variable**, puis sélectionnez **PIP3A2RequestMessage** dans la liste déroulante.  
  
9. Cliquez sur l'étiquette **Cliquez ici pour ajouter une nouvelle ligne** sous **Nom de la variable** sur la ligne suivante, puis sélectionnez **Contoso3A2ResponseMessage** dans la liste déroulante.  
  
10. Sélectionnez **Destination** dans le volet gauche, sélectionnez **PIP3A2ResponseMessage** à partir de la **nom de la Variable** liste déroulante, puis cliquez sur **OK**.  
  
11. Dans l'Explorateur de solutions, cliquez sur le fichier **ContosoResponse3A2RequestMerge.btm** , puis cliquez sur **Ouvrir avec**.  
  
12. Dans la boîte de dialogue **Ouvrir avec - ContosoResponse3A2RequestMerge.btm** , sélectionnez **Éditeur XML** dans la liste des programmes, puis cliquez sur **OK**. Cliquez sur **Oui**.  
  
    > [!NOTE]
    >  En raison du grand nombre de liens requis pour cette carte, ce didacticiel utilise [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 2008 l’éditeur HTML/XML pour construire le mappage en copiant manuellement les informations de mappage.  
  
13. Dans le menu **Edition** , cliquez sur **Sélectionner tout**.  
  
14. Copiez le code XML suivant dans le Presse-papiers. Dans le menu **Edition** , cliquez sur **Coller** pour remplacer le mappage actuel :  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <!-- Generated using BizTalk Mapper on Mon, Nov 08 2004 06:20:59 PM -->  
    <!-- Copyright (c) Microsoft Corporation.  All rights reserved. -->  
    <mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes"><SrcTree><xs:schema xmlns:tns="http://schemas.microsoft.com/BizTalk/2003/aggschema" xmlns:ns2="http://Contoso.com/Price" xmlns:ns1="http://schemas.microsoft.com/biztalk/btarn/2004/3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://schemas.microsoft.com/BizTalk/2003/aggschema" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:import schemaLocation="Microsoft.Solutions.BTARN.Schemas.RNPIPs._3A2PriceAndAvailabilityQueryMessageGuideline_v1_3" namespace="http://schemas.microsoft.com/biztalk/btarn/2004/3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd"/>  
    <xs:import schemaLocation="ContosoPriceAndAvailability.ContosoPriceSchema" namespace="http://Contoso.com/Price"/>  
    <xs:element name="Root">  
    <xs:complexType>  
    <xs:sequence>  
    <xs:element name="InputMessagePart_0">  
    <xs:complexType>  
    <xs:sequence>  
    <xs:element ref="ns1:Pip3A2PriceAndAvailabilityQuery"/>  
    </xs:sequence>  
    </xs:complexType>  
    </xs:element>  
    <xs:element name="InputMessagePart_1">  
    <xs:complexType>  
    <xs:sequence>  
    <xs:element ref="ns2:rootPriceResponse"/>  
    </xs:sequence>  
    </xs:complexType>  
    </xs:element>  
    </xs:sequence>  
    </xs:complexType>  
    </xs:element>  
    </xs:schema></SrcTree><TrgTree RootNode_Name="Pip3A2PriceAndAvailabilityResponse"><Reference Location="Microsoft.Solutions.BTARN.Schemas.RNPIPs._3A2PriceAndAvailabilityResponseMessageGuideline_v1_3"/></TrgTree><ScriptTypePrecedence><CSharp Enabled="Yes"/><ExternalAssembly Enabled="Yes"/><VbNet Enabled="Yes"/><JScript Enabled="Yes"/><XsltCallTemplate Enabled="Yes"/><Xslt Enabled="Yes"/></ScriptTypePrecedence><TreeValues><TestValues/><ConstantValues/></TreeValues><Pages><Page Name="Page 1"><Links><Link LinkID="1" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='GlobalProductStatusCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='GlobalProductStatusCode']" Label=""/><Link LinkID="2" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='unitPrice']/*[local-name()='FinancialAmount']/*[local-name()='GlobalCurrencyCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='unitPrice']/*[local-name()='FinancialAmount']/*[local-name()='GlobalCurrencyCode']" Label=""/><Link LinkID="3" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='ProductIdentification']/*[local-name()='GlobalProductIdentifier']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='ProductIdentification']/*[local-name()='GlobalProductIdentifier']" Label=""/><Link LinkID="4" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='ProductIdentification']/*[local-name()='PartnerProductIdentification']/*[local-name()='GlobalPartnerClassificationCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='ProductIdentification']/*[local-name()='PartnerProductIdentification']/*[local-name()='GlobalPartnerClassificationCode']" Label=""/><Link LinkID="5" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='ProductIdentification']/*[local-name()='PartnerProductIdentification']/*[local-name()='ProprietaryProductIdentifier']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='ProductIdentification']/*[local-name()='PartnerProductIdentification']/*[local-name()='ProprietaryProductIdentifier']" Label=""/><Link LinkID="6" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='LineNumber']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='LineNumber']" Label=""/><Link LinkID="7" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='GlobalPricingTypeCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='GlobalPricingTypeCode']" Label=""/><Link LinkID="8" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='thisDocumentIdentifier']/*[local-name()='ProprietaryDocumentIdentifier']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='requestingDocumentIdentifier']/*[local-name()='ProprietaryDocumentIdentifier']" Label=""/><Link LinkID="9" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='thisDocumentGenerationDateTime']/*[local-name()='DateTimeStamp']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='requestingDocumentDateTime']/*[local-name()='DateTimeStamp']" Label=""/><Link LinkID="10" LinkFrom="1" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='thisDocumentIdentifier']/*[local-name()='ProprietaryDocumentIdentifier']" Label=""/><Link LinkID="11" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='GlobalLocationIdentifier']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='GlobalLocationIdentifier']" Label=""/><Link LinkID="12" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='cityName']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='cityName']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="13" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='addressLine1']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='addressLine1']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="14" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='addressLine2']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='addressLine2']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="15" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='addressLine3']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='addressLine3']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="16" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='GlobalCountryCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='GlobalCountryCode']" Label=""/><Link LinkID="17" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='NationalPostalCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='NationalPostalCode']" Label=""/><Link LinkID="18" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='regionName']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='regionName']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="19" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='GlobalPartnerRoleClassificationCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='GlobalPartnerRoleClassificationCode']" Label=""/><Link LinkID="20" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='GlobalPartnerClassificationCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='GlobalPartnerClassificationCode']" Label=""/><Link LinkID="21" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalBusinessIdentifier']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalBusinessIdentifier']" Label=""/><Link LinkID="22" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalSupplyChainCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalSupplyChainCode']" Label=""/><Link LinkID="23" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='contactName']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='contactName']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="24" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='telephoneNumber']/*[local-name()='CommunicationsNumber']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='telephoneNumber']/*[local-name()='CommunicationsNumber']" Label=""/><Link LinkID="25" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='EmailAddress']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='EmailAddress']" Label=""/><Link LinkID="26" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='GlobalPartnerRoleClassificationCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='GlobalPartnerRoleClassificationCode']" Label=""/><Link LinkID="27" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='GlobalPartnerClassificationCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='GlobalPartnerClassificationCode']" Label=""/><Link LinkID="28" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalBusinessIdentifier']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalBusinessIdentifier']" Label=""/><Link LinkID="29" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalSupplyChainCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalSupplyChainCode']" Label=""/><Link LinkID="30" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='contactName']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='contactName']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="31" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='telephoneNumber']/*[local-name()='CommunicationsNumber']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='telephoneNumber']/*[local-name()='CommunicationsNumber']" Label=""/><Link LinkID="32" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='EmailAddress']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='EmailAddress']" Label=""/><Link LinkID="33" LinkFrom="2" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='thisDocumentGenerationDateTime']/*[local-name()='DateTimeStamp']" Label=""/><Link LinkID="34" LinkFrom="3" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='GlobalDocumentFunctionCode']" Label=""/><Link LinkID="35" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_1']/*[local-name()='rootPriceResponse']/*[local-name()='Products']/@*[local-name()='Price']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='unitPrice']/*[local-name()='FinancialAmount']/*[local-name()='MonetaryAmount']" Label=""/><Link LinkID="36" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_1']/*[local-name()='rootPriceResponse']/*[local-name()='Products']/@*[local-name()='NumberAvailable']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='ProductQuantity']" Label=""/><Link LinkID="37" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_1']/*[local-name()='rootPriceResponse']/*[local-name()='Products']/@*[local-name()='NumberAvailable']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseQuantity']/*[local-name()='ProductQuantity']" Label=""/></Links><Functoids><Functoid FunctoidID="1" X-Cell="52" Y-Cell="231" Functoid-FID="260" Functoid-Name="Scripting" Label=""><Input-Parameters/><ScripterCode><Script Language="CSharp"><![CDATA[///*Uncomment the following code for a sample Inline C# function  
    //that concatenates two inputs. Change the number of parameters of  
    //this function to be equal to the number of inputs connected to this functoid.*/  
  
    public string returnGUID()  
    {  
    return System.Guid.NewGuid().ToString();  
    }]]></Script></ScripterCode></Functoid><Functoid FunctoidID="2" X-Cell="55" Y-Cell="236" Functoid-FID="260" Functoid-Name="Scripting" Label=""><Input-Parameters/><ScripterCode><Script Language="CSharp"><![CDATA[public string GetRNDateTime()  
    {  
    DateTime dt;  
    dt=DateTime.UtcNow;  
    string dateVal = dt.ToString("u");  
    dateVal = dateVal.Replace("-","");  
    dateVal = dateVal.Replace(":","");  
    dateVal  =dateVal.Replace(" ","T");  
    string sec = "."+ DateTime.UtcNow.Millisecond.ToString()+"Z";  
    dateVal  =dateVal.Replace("Z",sec);  
    return  dateVal;  
    }]]></Script></ScripterCode></Functoid><Functoid FunctoidID="3" X-Cell="54" Y-Cell="239" Functoid-FID="107" Functoid-Name="String Concatenate" Label=""><Input-Parameters><Parameter Type="Constant" Value="Response" Guid="{FA85B113-6FB4-4932-A125-5CF751A536B5}"/></Input-Parameters></Functoid></Functoids></Page></Pages></mapsource>  
    ```  
  
15. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
### <a name="to-configure-the-expression1-shape"></a>Pour configurer la forme Expression_1  
  
1.  Dans l'Explorateur de solutions, double-cliquez sur **PrivateResponder.odx**.  
  
2.  Sur l'aire de conception de l'orchestration, double-cliquez sur la forme **Expression_1** pour ouvrir l'Éditeur d'expression BizTalk.  
  
3.  Dans l'Éditeur d'expression BizTalk, tapez le code suivant :  
  
    ```  
    contosoResponseXML = PIP3A2ResponseMessage;  
  
    submitMessage.SubmitMessage(  
      Microsoft.Solutions.BTARN.Shared.MessageCategory.AsyncResponse,  
    ActionMessage(Microsoft.Solutions.BTARN.GlobalSchemas.SCDestinationPartnerID),  
    ActionMessage(Microsoft.Solutions.BTARN.GlobalSchemas.SCSourcePartnerID),  
    ActionMessage(Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode),  
    ActionMessage(Microsoft.Solutions.BTARN.GlobalSchemas.SCInstanceID),  
    ActionMessage(Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPVersion),   
    Helper.ReturnSCWithDocType(contosoResponseXML) );  
    ```  
  
4.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 7 : Création et configuration des Ports](../../adapters-and-accelerators/accelerator-rosettanet/step-7-creating-and-configuring-ports.md)