---
title: "En savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, connection string
- ADO, connection string
ms.assetid: 7a46eaae-604f-4bae-924b-9f6d43a6e8a0
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1a27fa8b09addc7874e6056f0b467c7f874a41e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="read-about-data-provider-types-for-the-sap-connection-string"></a>En savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP
Pour établir la connexion à un système SAP, ADO.NET clients doivent spécifier les propriétés de connexion SAP sous la forme d’une chaîne de connexion. Le format de la chaîne de connexion SAP ressemble à :  
  
```  
[Property1]=[Value1];[Property2]=[Value2];....  
```  
  
 La chaîne de connexion pour se connecter à un système SAP à l’aide du [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] peut avoir les types suivants :  
  
-   **R : le TYPE** une connexion basée sur l’hôte d’application dans laquelle l’URI de connexion spécifie un serveur d’applications par le biais duquel le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] se connecte au système SAP.  
  
-   **TYPE B:** une connexion avec équilibrage de charge dans lequel l’URI de connexion spécifie un serveur de messages par le biais duquel le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] se connecte au système SAP.  
  
-   **TYPE D:** une connexion de destination dans lequel l’URI de connexion spécifie une destination dans le fichier saprfc.ini qui contient les paramètres de connexion pour le système SAP.  
  
 Le tableau suivant décrit la façon dont ces connexions sont spécifiées dans l’URI de connexion.  
  
|TYPE|Propriété 1|Propriété 2| Description|  
|----------|----------------|----------------|-----------------|  
|Un|ASHOST (hôte d’Application serveur)|SYSNR (numéro du système SAP)|Spécifie une connexion basée sur l’hôte d’application.|  
|B|MSHOST (hôte de serveur de Message)|R3NAME (nom de R3 SAP)|Spécifie une connexion via un serveur de messages d’équilibrage de charge. Pour une connexion d’équilibrage de charge, vous pouvez spécifier un groupe de serveur facultative.|  
|D|CIBLE qui contient les paramètres de connexion dans le fichier saprfc.ini|-|Spécifie une connexion basée sur la destination. Les paramètres de connexion SAP sont contenus dans la destination spécifiée dans le fichier saprfc.ini. Seules les connexions de TYPE A et B de TYPE peuvent être spécifiées dans la destination. **Remarque :** si vous spécifiez des valeurs de connexion dans le fichier saprfc.ini, assurez-vous que le fichier se trouve dans le même dossier que le .exe qui accède au fichier ou à un emplacement standard comme requis par le système SAP. Pour plus d’informations, consultez la documentation de SAP.|  
  
 En fonction du type de connexion, la chaîne de connexion pour se connecter à un système SAP à l’aide du [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] peut contenir les propriétés suivantes.  
  
|Propriété|Utilisé pour le TYPE| Description|  
|--------------|-------------------|-----------------|  
|Application hôte du serveur (ASHOST)|Un|Nom de l’hôte de serveur d’applications SAP.|  
|Numéro du système (SYSNR)|Un|Le numéro du système SAP|  
|Nom de groupe serveur d’applications (groupe)|B|Nom du groupe de serveurs SAP. Il s’agit d’un groupe facultatif de serveurs d’applications dans une connexion d’équilibrage de charge.|  
|Hôte du serveur de message (MSHOST)|B|Nom de l’hôte de serveur de message SAP|  
|Service de serveur de message (MSSERV)|B|Nom du service de serveur de message SAP comme spécifié dans le \<lecteur système > : \WINDOWS\system32\drivers\etc\services fichier. Si vous ne spécifiez pas une valeur, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] suppose que ce soit « sapms\<nom du système r/3 > ». Par exemple, si le nom du système r/3 est DV1, l’adaptateur suppose que le nom de service de serveur de message pour être « sapmsDV1 ».<br /><br /> Toutefois, si l’entrée dans le fichier de services est différente, vous devez spécifier cette valeur.|  
|Nom du système r/3 (R3NAME)|B|Le nom SAP r/3.|  
|Destination (destination)|D|Récupère les paramètres de connexion à partir du fichier saprfc.ini.|  
|Client (CLIENT)|A, B, D|Le numéro de client SAP|  
|Language (langue)|A, B, D|Langage|  
|Mot de passe (mot de passe)|A, B, D|Le mot de passe utilisateur SAP|  
|Nom d’utilisateur (utilisateur)|A, B, D|Le nom d’utilisateur pour se connecter à un système SAP|  
|Activer l’interface utilisateur graphique SAP débogage (AbapDebug)|A, B, D|Paramètre facultatif qui spécifie si ABAP débogage à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] est activée et si l’adaptateur utilise l’interface utilisateur graphique SAP pour le débogage. La valeur peut être True ou False ; Si la valeur est True, ABAP le débogage est activé et l’interface utilisateur graphique SAP s’ouvre. La valeur par défaut est False.|  
|Trace RFC SDK(RfcSdkTrace)|A, B, D|Paramètre facultatif qui spécifie si le suivi de RFC bibliothèque est activé. La valeur peut être True ou False ; Si la valeur est True, le suivi de RFC bibliothèque est activé. La valeur par défaut est False.|  
  
> [!NOTE]
>  Les valeurs fournies dans les parenthèses dans la colonne de propriété sont le nom des propriétés de connexion doit être spécifiée tout en fournissant l’URI de connexion via une solution de programmation. Toutefois, si vous utilisez le plug-in DDEX ou l’Assistant Exportation et importation de SQL Server à utiliser l’interface ADO, les propriétés de connexion sont répertoriées en tant que noms conviviaux.  
  
## <a name="example-connection-string-for-type-a"></a>Exemple de chaîne de connexion pour le TYPE A  
 Un exemple de chaîne de connexion pour le TYPE A ressemble à :  
  
```  
TYPE=A; ASHOST=SAPSERVER; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  
  
> [!NOTE]
>  Par défaut le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] toujours considère que la chaîne de connexion de TYPE a.  
  
## <a name="example-connection-string-for-type-b"></a>Exemple de chaîne de connexion pour le TYPE B  
 Un exemple de chaîne de connexion pour le TYPE B doit ressembler à :  
  
```  
TYPE=B; R3NAME=NAME1; GROUP=ADAPTER; MSHOST=MSSERVER; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  
  
## <a name="example-connection-string-for-type-d"></a>Exemple de chaîne de connexion pour le TYPE D  
 Un exemple de chaîne de connexion pour le TYPE D ressemble à :  
  
```  
TYPE=D; DEST=TESTSAPSRV; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  
  
 Un exemple de fichier saprfc.ini ressemble à :  
  
```  
DEST=TESTSAPSRV  
TYPE=A  
ASHOST=ADAPSAP47  
SYSNR=00  
```  
  
 Pour plus d’informations sur le fichier saprfc.ini, consultez [http://go.microsoft.com/fwlink/?LinkId=91457](http://go.microsoft.com/fwlink/?LinkId=91457).  
  
 Le mot de passe pour tous les types de connexion ne doit pas contenir de guillemets doubles. Toutefois, si le mot de passe contient d’autres caractères spéciaux, le mot de passe doit être placé entre guillemets doubles. Exemple :  
  
```  
ASHOST=SAPSERVER; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=",@/:;_ \\";  
```  
  
> [!IMPORTANT]
>  Vous devez spécifier les paramètres de connexion pour une seule connexion TYPE A, B ou D. Par exemple, si vous spécifiez le serveur d’Application hôte dans la chaîne de connexion, vous ne devez pas spécifier un nom d’hôte de serveur de Message ou le R3NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)