---
title: "Propriétés de configuration des adaptateurs BizTalk intégrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, security
- adapters, passwords
- IReceiveLocation.CustomData property
- security, passwords
- ISendPort.CustomData property
- binding files, passwords
- adapters, properties
- binding files, security
ms.assetid: 4780a558-4322-428a-aa4a-0c32913faded
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6da0c7ae3899c71ab000bc30cb6d801aa856f83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-properties-for-integrated-biztalk-adapters"></a><span data-ttu-id="ec764-102">Propriétés de configuration des adaptateurs BizTalk intégrés</span><span class="sxs-lookup"><span data-stu-id="ec764-102">Configuration Properties for Integrated BizTalk Adapters</span></span>
<span data-ttu-id="ec764-103">Le modèle d’objet de l’Explorateur BizTalk expose le **IReceiveLocation.CustomData** et **ISendPort.CustomData** propriétés qui contiennent le sac de propriétés de configuration de l’adaptateur sous la forme d’une nom/valeur. paire de chaîne XML.</span><span class="sxs-lookup"><span data-stu-id="ec764-103">The BizTalk Explorer object model exposes the **IReceiveLocation.CustomData** and **ISendPort.CustomData** properties that contain the adapter configuration property bag in the form of a name/value pair XML string.</span></span> <span data-ttu-id="ec764-104">Cette paire nom/valeur chaîne XML est stockée dans un \<CustomProps > élément au sein d’un \<TransportTypeData > élément dans un fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="ec764-104">This name/value pair XML string is stored in a \<CustomProps> element within a \<TransportTypeData> element in a binding file.</span></span> <span data-ttu-id="ec764-105">La plupart des informations contenues dans le \<CustomProps > élément correspond aux informations qui peuvent être définies pour un adaptateur dans l’interface utilisateur de BizTalk Server (par exemple, la Console Administration de BizTalk ou de l’Explorateur BizTalk).</span><span class="sxs-lookup"><span data-stu-id="ec764-105">Most of the information in the \<CustomProps> element corresponds to information that can be set for an adapter in the BizTalk Server user interface (such as the BizTalk Administration Console or BizTalk Explorer).</span></span> <span data-ttu-id="ec764-106">Si ces valeurs sont présentes dans un fichier de liaison, elles sont appliquées à la configuration des adaptateurs pour les emplacements de réception et les ports d'envoi spécifiés lors de l'importation du fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="ec764-106">If these values are present in a binding file then they are applied to the adapter configuration for the specified receive locations and send ports when the binding file is imported.</span></span> <span data-ttu-id="ec764-107">Les informations de configuration de tous les adaptateurs sont enregistrées dans la base de données de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="ec764-107">Configuration information for all adapters is stored in the Single Sign-On database.</span></span>  
  
 <span data-ttu-id="ec764-108">Cette section décrit les propriétés pouvant être définies pour chaque adaptateur BizTalk intégré.</span><span class="sxs-lookup"><span data-stu-id="ec764-108">This section describes the configuration properties that can be set for each integrated BizTalk adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec764-109">Les informations de mot de passe qui sont stockées dans le \<TransportTypeData > élément d’un fichier de liaison est masquée afin que les données sensibles ne sont pas enregistrées en texte clair.</span><span class="sxs-lookup"><span data-stu-id="ec764-109">Password information that is stored in the \<TransportTypeData> element of a binding file is masked so that sensitive data is not saved in clear text.</span></span> <span data-ttu-id="ec764-110">En fonction du transport, ces informations sont soit remplacées par NULL, soit remplacées par des astérisques.</span><span class="sxs-lookup"><span data-stu-id="ec764-110">Depending on the transport, password information is either replaced with NULL or is replaced with asterisks.</span></span> <span data-ttu-id="ec764-111">Vous devez les entrer manuellement dans le fichier de liaison avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.</span><span class="sxs-lookup"><span data-stu-id="ec764-111">You must manually enter this information in the binding file to update the adapter configuration before importing the binding file into the target BizTalk Server configuration.</span></span>  
  
 <span data-ttu-id="ec764-112">Les données de configuration des adaptateurs conçus à l’aide de l’infrastructure d’adaptateurs sont stockées dans un \<AdapterConfig > élément.</span><span class="sxs-lookup"><span data-stu-id="ec764-112">The configuration data for adapters built using the Adapter Framework is stored in an \<AdapterConfig> element.</span></span> <span data-ttu-id="ec764-113">Étant donné que la \<AdapterConfig > élément spécifie le VT_BSTR (vt = « 8 ») type de données, le  **\<  >**  caractères contenus dans cet élément doivent être échappés ou une erreur se produit lorsque vous tentez Importez le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="ec764-113">Since the \<AdapterConfig> element specifies the VT_BSTR (vt="8") data type, the **\< >** characters contained in this element must be escaped or an error will occur when you attempt to import the binding file.</span></span> <span data-ttu-id="ec764-114">L'utilisation de ces caractères d'échappement rend les données de configuration moins faciles à lire pour l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ec764-114">This causes the text for the configuration data to be less human readable than if these characters were not escaped.</span></span> <span data-ttu-id="ec764-115">L'exemple suivant, portant sur les données de configuration d'un port d'envoi lié à l'adaptateur POP3, illustre ce fait.</span><span class="sxs-lookup"><span data-stu-id="ec764-115">The following example illustrates the effect of escaping these characters from sample configuration data for a send port bound to the POP3 adapter.</span></span>  
  
 <span data-ttu-id="ec764-116">**Données de configuration TransportTypeData n’échappement pas les caractères <> utilisés dans le \<AdapterConfig > élément**</span><span class="sxs-lookup"><span data-stu-id="ec764-116">**TransportTypeData configuration data that does not escape the <> characters used in the \<AdapterConfig> element**</span></span>  
  
 <span data-ttu-id="ec764-117">Ces données de configuration ne sont pas valides, car le \<AdapterConfig > élément spécifie le VT_BSTR (vt = « 8 ») type de données et la \< > caractères contenus dans le \<AdapterConfig > élément ne sont pas ignorés :</span><span class="sxs-lookup"><span data-stu-id="ec764-117">This configuration data is invalid because the \<AdapterConfig> element specifies the VT_BSTR (vt="8") data type and the \< > characters contained in the \<AdapterConfig> element are not escaped:</span></span>  
  
```  
<TransportTypeData>  
<CustomProps>  
<AdapterConfig vt="8">  
<Config xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
<mailServer>test.microsoft.com</mailServer>  
<serverPort>0</serverPort>  
<userName>testuser</userName>  
<password>******</password>  
<authenticationScheme>Basic</authenticationScheme>  
<sslRequired>false</sslRequired>  
<applyMIME>true</applyMIME>  
<bodyPartContentType>text/xml</bodyPartContentType>  
<bodyPartIndex>1</bodyPartIndex>  
<errorThreshold>10</errorThreshold>  
<pollingInterval>5</pollingInterval>  
<pollingUnitOfMeasure>Minutes</pollingUnitOfMeasure>   
<uri>POP3://test.microsoft.com#testuser</uri>  
</Config>  
</AdapterConfig>  
</CustomProps>  
</TransportTypeData>  
```  
  
 <span data-ttu-id="ec764-118">**Données de configuration TransportTypeData échappement les caractères <> utilisés dans le \<AdapterConfig > élément**</span><span class="sxs-lookup"><span data-stu-id="ec764-118">**TransportTypeData configuration data that does escape the <> characters used in the \<AdapterConfig> element**</span></span>  
  
 <span data-ttu-id="ec764-119">Étant donné que la \<AdapterConfig > élément spécifie le VT_BSTR (vt = « 8 ») type de données, le \< > caractères doivent être échappés à partir de la \<AdapterConfig > élément tel qu’illustré ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="ec764-119">Since the \<AdapterConfig> element specifies the VT_BSTR (vt="8") data type, the \< > characters must be escaped from the \<AdapterConfig> element as seen below:</span></span>  
  
```  
<TransportTypeData>  
<CustomProps>  
<AdapterConfig vt="8">  
<Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
xmlns:xsd="http://www.w3.org/2001/XMLSchema"><mailServer>test  
microsoft.com</mailServer><serverPort>0</serverPort>&  
lt;userName>testuser</userName><password>******</pass  
word><authenticationScheme>Basic</authenticationScheme>&  
lt;sslRequired>false</sslRequired><applyMIME>true</ap  
plyMIME><bodyPartContentType>text/xml</bodyPartContentType&  
gt;<bodyPartIndex>1</bodyPartIndex><errorThreshold>10  
</errorThreshold><pollingInterval>5</pollingInterval>  
<pollingUnitOfMeasure>Minutes</pollingUnitOfMeasure><uri  
>POP3://test.microsoft.com#testuser</uri></Config>  
</AdapterConfig>  
</CustomProps>  
</TransportTypeData>  
```  
  
 <span data-ttu-id="ec764-120">Les adaptateurs intégrés créés avec l'infrastructure d'adaptateurs sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="ec764-120">The integrated adapters that were created with the Adapter Framework include the following:</span></span>  
  
-   <span data-ttu-id="ec764-121">adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="ec764-121">FTP Adapter</span></span>  
  
-   <span data-ttu-id="ec764-122">Adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="ec764-122">MQSeries Adapter</span></span>  
  
-   <span data-ttu-id="ec764-123">Adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="ec764-123">MSMQ Adapter</span></span>  
  
-   <span data-ttu-id="ec764-124">Adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="ec764-124">POP3 Adapter</span></span>  
  
-   <span data-ttu-id="ec764-125">Adaptateur Windows Sharepoint Services</span><span class="sxs-lookup"><span data-stu-id="ec764-125">Windows Sharepoint Services Adapter</span></span>  
  
 <span data-ttu-id="ec764-126">Pour afficher un exemple de chaîne utilisée comme données de configuration TransportTypeData pour chaque adaptateur intégré, reportez-vous à la rubrique sur les propriétés de configuration associée à l'adaptateur de cette section.</span><span class="sxs-lookup"><span data-stu-id="ec764-126">To view a sample string used as the TransportTypeData configuration data for each integrated adapter, please see the configuration properties topic that is associated with the adapter in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec764-127">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ec764-127">In This Section</span></span>  
 [<span data-ttu-id="ec764-128">Types de Variable de propriété de configuration</span><span class="sxs-lookup"><span data-stu-id="ec764-128">Configuration Property Variable Types</span></span>](../core/configuration-property-variable-types.md)  
  
 [<span data-ttu-id="ec764-129">Propriétés de Configuration de l’adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="ec764-129">File Adapter Configuration Properties</span></span>](../core/file-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="ec764-130">Propriétés de Configuration de l’adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="ec764-130">FTP Adapter Configuration Properties</span></span>](../core/ftp-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="ec764-131">Propriétés de Configuration de l’adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="ec764-131">HTTP Adapter Configuration Properties</span></span>](../core/http-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="ec764-132">Propriétés de Configuration de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="ec764-132">MQSeries Adapter Configuration Properties</span></span>](../core/mqseries-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="ec764-133">Propriétés de Configuration de l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="ec764-133">MSMQ Adapter Configuration Properties</span></span>](../core/msmq-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="ec764-134">POP3 Propriétés de Configuration de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="ec764-134">POP3 Adapter Configuration Properties</span></span>](../core/pop3-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="ec764-135">Propriétés de Configuration de l’adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="ec764-135">SMTP Adapter Configuration Properties</span></span>](../core/smtp-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="ec764-136">Propriétés de Configuration de l’adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="ec764-136">SOAP Adapter Configuration Properties</span></span>](../core/soap-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="ec764-137">Propriétés de Configuration de l’adaptateur Windows Sharepoint Services</span><span class="sxs-lookup"><span data-stu-id="ec764-137">Windows Sharepoint Services Adapter Configuration Properties</span></span>](../core/windows-sharepoint-services-adapter-configuration-properties.md)