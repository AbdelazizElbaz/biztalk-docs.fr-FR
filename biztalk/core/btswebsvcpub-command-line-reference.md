---
title: Référence de ligne de commande BTSWebSvcPub | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5e19dd4d-9f2c-4a17-9437-8701e1c274fb
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c9993092c0d798ae2d47f614a24da21c3a2df62
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="btswebsvcpub-command-line-reference"></a>Référence de la ligne de commande BTSWebSvcPub
Cette rubrique contient des informations de référence relatives à l'outil de ligne de commande BTSWebSvcPub inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez utiliser BTSWebSvcPub pour créer des services Web (.asmx) et publier des orchestrations via les services Web comme suit :  
  
## <a name="usage"></a>Utilisation  
 **BTSWebSvcPub PathName [-Location:** *value* **] [-Overwrite] [-Anonymous]**  
  
 **[-Name:** *value* **] [-Namespace:** *value* **] [-TargetNamespace:** *value* **]**  
  
 **[-UnknownHeaders[** *+* **&#124;** *-* **]] [-SingleSignOn[** *+* **&#124;** *-* **]] [-ParameterStyle:** *value* **]**  
  
 **[-ConformanceClaims:** *value* **] [-ForceRequestResponse:** *value* **] [-ReceiveLocation]**  
  
 **[-ApplicationName:** *value* **]**  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis| Description|  
|---------------|--------------|-----------------|  
|**Chemin d’accès**|Oui|Chemin d’accès et nom de fichier d’assembly BizTalk (*.dll) ou la description du service web (\*.xml) fichier.|  
|**-Location**|non|Emplacement de publication. (Syntaxe : « http://host[:port]/path »)|  
|**-Overwrite**|non|Remplacer l'emplacement spécifié.|  
|**-Anonymous**|non|Autoriser l'accès anonyme au service Web.|  
|**-Name**|non|Nom de la solution et de l'assembly (fichiers .sln et .dll) qui contiendront le service Web.|  
|**-Namespace**|non|Espace de noms par défaut pour le code du service Web.|  
|**-Targetnamespace**|non|Espace de noms cible du service Web. (Exemple :'http://www.northwindtraders.com')|  
|**-UnknownHeaders**|non|Prendre en charge les en-têtes SOAP inconnus.|  
|**-SinglesSignon**|non|Prendre en charge les en-têtes SOAP d'authentification unique SharePoint Portal Server.|  
|**-ParameterStyle**|non|SoapParameterStyle pour les messages : « Default », « Bare » ou « Wrapped ».|  
|**-ConfirmanceClaims**|non|Revendication de l’interopérabilité des services Web (WSI) : « None » ou « BasicProfile1_1 ».|  
|**-ForceRequestResponse**|non|Exposer des opérations BizTalk unidirectionnelles en tant que méthodes Web de requête-réponse.|  
|**-ReceiveLocation**|non|Permet de créer des emplacements de réception dans l'application BizTalk spécifiée.|  
|**-ApplicationName**|non|Nom de l'application BizTalk dans laquelle créer des emplacements de réception. Si cette valeur n'est pas définie, l'application BizTalk par défaut est utilisée.|  
  
## <a name="sample"></a>Exemple  
 BTSWebSvcPub.exe "MyAssembly.dll" -Location:http://localhost/MyVdir  
  
 -Overwrite  
  
## <a name="remarks"></a>Notes  
 Les noms de paramètres ne respectent pas la casse et peuvent être abrégés. Les valeurs de paramètre respectent la casse.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment utiliser l’Assistant Publication de Services Web BizTalk pour publier une Orchestration en tant que Service Web](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)