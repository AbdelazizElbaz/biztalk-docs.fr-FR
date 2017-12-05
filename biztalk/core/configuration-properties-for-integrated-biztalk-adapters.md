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
ms.openlocfilehash: 950f244c3a46af87164c4e276a50cd7a91fee14b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="configuration-properties-for-integrated-biztalk-adapters"></a>Propriétés de configuration des adaptateurs BizTalk intégrés
Le modèle d’objet de l’Explorateur BizTalk expose le **IReceiveLocation.CustomData** et **ISendPort.CustomData** propriétés qui contiennent le sac de propriétés de configuration de l’adaptateur sous la forme d’une nom/valeur. paire de chaîne XML. Cette paire nom/valeur chaîne XML est stockée dans un \<CustomProps\> élément au sein d’un \<TransportTypeData\> élément dans un fichier de liaison. La plupart des informations contenues dans le \<CustomProps\> élément correspond aux informations qui peuvent être définies pour un adaptateur dans l’interface utilisateur de BizTalk Server (par exemple, la Console Administration de BizTalk ou de l’Explorateur BizTalk). Si ces valeurs sont présentes dans un fichier de liaison, elles sont appliquées à la configuration des adaptateurs pour les emplacements de réception et les ports d'envoi spécifiés lors de l'importation du fichier de liaison. Les informations de configuration de tous les adaptateurs sont enregistrées dans la base de données de l'authentification unique.  
  
 Cette section décrit les propriétés pouvant être définies pour chaque adaptateur BizTalk intégré.  
  
> [!NOTE]
>  Les informations de mot de passe qui sont stockées dans le \<TransportTypeData\> élément d’un fichier de liaison est masquée afin que les données sensibles ne sont pas enregistrées en texte clair. En fonction du transport, ces informations sont soit remplacées par NULL, soit remplacées par des astérisques. Vous devez les entrer manuellement dans le fichier de liaison avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.  
  
 Les données de configuration des adaptateurs conçus à l’aide de l’infrastructure d’adaptateurs sont stockées dans un \<AdapterConfig\> élément. Étant donné que la \<AdapterConfig\> élément spécifie le VT_BSTR (vt = « 8 ») type de données, le  **\< \>**  caractères contenus dans cet élément doivent être échappés ou une erreur se produit lorsque vous Essayez d’importer le fichier de liaison. L'utilisation de ces caractères d'échappement rend les données de configuration moins faciles à lire pour l'utilisateur. L'exemple suivant, portant sur les données de configuration d'un port d'envoi lié à l'adaptateur POP3, illustre ce fait.  
  
 **Données de configuration TransportTypeData n’échappement pas les caractères <> utilisés dans le \<AdapterConfig\> élément**  
  
 Ces données de configuration ne sont pas valides, car le \<AdapterConfig\> élément spécifie le VT_BSTR (vt = « 8 ») type de données et la \< \> caractères contenus dans le \<AdapterConfig\> élément ne sont pas ignorés :  
  
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
  
 **Données de configuration TransportTypeData échappement les caractères <> utilisés dans le \<AdapterConfig\> élément**  
  
 Étant donné que la \<AdapterConfig\> élément spécifie le VT_BSTR (vt = « 8 ») type de données, le \< \> caractères doivent être échappés à partir de la \<AdapterConfig\> élément tel qu’illustré ci-dessous :  
  
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
  
 Les adaptateurs intégrés créés avec l'infrastructure d'adaptateurs sont les suivants :  
  
-   adaptateur FTP  
  
-   Adaptateur MQSeries  
  
-   Adaptateur MSMQ  
  
-   Adaptateur POP3  
  
-   Adaptateur Windows Sharepoint Services  
  
 Pour afficher un exemple de chaîne utilisée comme données de configuration TransportTypeData pour chaque adaptateur intégré, reportez-vous à la rubrique sur les propriétés de configuration associée à l'adaptateur de cette section.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Types de variables des propriétés de configuration](../core/configuration-property-variable-types.md)  
  
 [Propriétés de configuration de l’adaptateur de fichier](../core/file-adapter-configuration-properties.md)  
  
 [Propriétés de configuration de l’adaptateur FTP](../core/ftp-adapter-configuration-properties.md)  
  
 [Propriétés de configuration de l’adaptateur HTTP](../core/http-adapter-configuration-properties.md)  
  
 [Propriétés de configuration de l’adaptateur MQSeries](../core/mqseries-adapter-configuration-properties.md)  
  
 [Propriétés de configuration de l’adaptateur MSMQ](../core/msmq-adapter-configuration-properties.md)  
  
 [Propriétés de configuration de l’adaptateur POP3](../core/pop3-adapter-configuration-properties.md)  
  
 [Propriétés de configuration de l’adaptateur SMTP](../core/smtp-adapter-configuration-properties.md)  
  
 [Propriétés de configuration de l’adaptateur SOAP](../core/soap-adapter-configuration-properties.md)  
  
 [Propriétés de configuration de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-configuration-properties.md)