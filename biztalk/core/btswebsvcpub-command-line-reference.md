---
title: "Référence de ligne de commande BTSWebSvcPub | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e19dd4d-9f2c-4a17-9437-8701e1c274fb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c9993092c0d798ae2d47f614a24da21c3a2df62
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btswebsvcpub-command-line-reference"></a>Référence de la ligne de commande BTSWebSvcPub
Cette rubrique contient des informations de référence relatives à l'outil de ligne de commande BTSWebSvcPub inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez utiliser BTSWebSvcPub pour créer des services Web (.asmx) et publier des orchestrations via les services Web comme suit :  
  
## <a name="usage"></a>Utilisation  
 **BTSWebSvcPub PathName [-emplacement :** *valeur* **] [-remplacer] [-anonyme]**  
  
 **[-Nom :** *valeur* **] [-Namespace :** *valeur* **] [-TargetNamespace :** *valeur* **]**  
  
 **[-UnknownHeaders [**  *+*  **&#124;**  *-*  **]] [-SingleSignOn [**  *+*  **&#124;**  *-*  **]] [-ParameterStyle :** *valeur* **]**  
  
 **[-ConformanceClaims :** *valeur* **] [-ForceRequestResponse :** *valeur* **] [-emplacement de réception]**  
  
 **[-ApplicationName :** *valeur* **]**  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis| Description|  
|---------------|--------------|-----------------|  
|**PathName**|Oui|Chemin d’accès et nom de fichier d’assembly BizTalk (*.dll) ou la description du service web (\*.xml) fichier.|  
|**-Location**|Non|Emplacement de publication. (Syntaxe : « http://host[:port]/path »)|  
|**-Remplacer**|Non|Remplacer l'emplacement spécifié.|  
|**-Anonyme**|Non|Autoriser l'accès anonyme au service Web.|  
|**-Nom**|Non|Nom de la solution et de l'assembly (fichiers .sln et .dll) qui contiendront le service Web.|  
|**-Namespace**|Non|Espace de noms par défaut pour le code du service Web.|  
|**-Targetnamespace**|Non|Espace de noms cible du service Web. (Exemple : « http://www.northwindtraders.com »)|  
|**-UnknownHeaders**|Non|Prendre en charge les en-têtes SOAP inconnus.|  
|**-SinglesSignon**|Non|Prendre en charge les en-têtes SOAP d'authentification unique SharePoint Portal Server.|  
|**-ParameterStyle**|Non|SoapParameterStyle pour les messages : « Default », « Bare » ou « Wrapped ».|  
|**-ConfirmanceClaims**|Non|Revendication de l’interopérabilité des services Web (WSI) : « None » ou « BasicProfile1_1 ».|  
|**-ForceRequestResponse**|Non|Exposer des opérations BizTalk unidirectionnelles en tant que méthodes Web de requête-réponse.|  
|**L’emplacement de réception-**|Non|Permet de créer des emplacements de réception dans l'application BizTalk spécifiée.|  
|**-ApplicationName**|Non|Nom de l'application BizTalk dans laquelle créer des emplacements de réception. Si cette valeur n'est pas définie, l'application BizTalk par défaut est utilisée.|  
  
## <a name="sample"></a>Exemple  
 BTSWebSvcPub.exe "MyAssembly.dll" -Location:http://localhost/MyVdir  
  
 -Overwrite  
  
## <a name="remarks"></a>Notes  
 Les noms de paramètres ne respectent pas la casse et peuvent être abrégés. Les valeurs de paramètre respectent la casse.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment utiliser l’Assistant Publication de Services Web BizTalk pour publier une Orchestration en tant que Service Web](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)