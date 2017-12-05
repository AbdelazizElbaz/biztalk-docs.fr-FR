---
title: "Assistant Registre d’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- utilities, Adapter Registration Wizard
- Adapter Registration Wizard
ms.assetid: bd15d0c7-01bb-41f9-9157-cdcf4bb4e39a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b721294acb07d4c69c5b2ae7b58b0e135625eee8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="adapter-registry-wizard"></a>Assistant Registre d’adaptateur
L'Assistant Registre de l'adaptateur permet de créer les fichiers de Registre nécessaires pour configurer et inscrire un adaptateur personnalisé.  
  
## <a name="location-in-sdk"></a>Emplacement dans le kit de développement logiciel (SDK)  
 *\<Chemin d’installation\>*\SDK\Utilities\AdapterRegistryWizard\  
  
## <a name="to-run-this-utility"></a>Exécution de cet utilitaire  
 Démarrez l'Assistant en exécutant le fichier exécutable AdapterRegistryWizard.exe. Les pages qui suivent vous demandent des informations concernant votre adaptateur et les propriétés qu'il prend en charge. Chacune des pages de l'Assistant Registre de l'adaptateur est décrite dans les sections ci-dessous.  
  
### <a name="generic-adapter-properties-page"></a>Page Propriétés de l'adaptateur  
 Utilisez la page Propriétés de l'adaptateur pour spécifier les propriétés de l'adaptateur.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Type d’adaptateur de transport**|Spécifier le type de l'adaptateur.|  
|**Espace de noms de propriété**|Spécifiez l’espace de noms de l’adaptateur. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]stocke les propriétés spécifiques à l’adaptateur dans le contexte de message dans cet espace de noms.|  
|**Il peut recevoir des messages et les envoyer à BizTalk Server**|Identifier les modèles de communication pris en charge par l'adaptateur. Utilisée pour calculer l'entrée de registre Contraintes de l'adaptateur.|  
|**L’adaptateur peut envoyer des messages à partir de BizTalk Server**|Identifier les modèles de communication pris en charge par l'adaptateur. Utilisée pour calculer l'entrée de registre Contraintes de l'adaptateur.|  
  
### <a name="inbound-part-page"></a>Page Partie entrante  
 Utilisez la page Partie entrante pour spécifier la logique de réception entrante de votre adaptateur.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Parcourir**|Sélectionner l'assembly qui implémente la logique de réception entrante de votre adaptateur. Une liste de types publics exposés par cet assembly s’affichent dans la liste déroulante. Dans cette liste déroulante, sélectionnez le type dans l'assembly spécifié qui implémente la logique entrante de cet adaptateur.|  
|**L’adaptateur prend en charge le protocole de demande-réponse**|Spécifier les fonctions de réception de votre adaptateur. Utilisée pour calculer l'entrée de Registre Contraintes de votre adaptateur.|  
|**L’adaptateur est isolé (qui est hébergé dans un autre processus)**|Spécifier les fonctions de réception de votre adaptateur. Utilisée pour calculer l'entrée de Registre Contraintes de votre adaptateur.|  
  
### <a name="outbound-part-page"></a>Page Partie sortante  
 Utilisez la page Partie sortante pour spécifier la logique de réception sortante de votre adaptateur.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Parcourir**|Sélectionner l'assembly qui implémente la logique de réception sortante de votre adaptateur. Une liste de types publics exposés par cet assembly apparaît dans la liste déroulante. Dans cette liste déroulante, sélectionnez le type de l'assembly spécifié qui implémente la logique sortante de cet adaptateur. Vous devez également entrer une liste d'alias séparés par des virgules pour identifier le protocole utilisé par cet adaptateur (par exemple, envoyer://).|  
|**L’adaptateur prend en charge le protocole sollicitation-réponse**|Identifier les fonctions de transmission de votre adaptateur. Ces valeurs sont utilisées pour calculer l'entrée de registre Contraintes de votre adaptateur.|  
  
### <a name="adapter-management-page"></a>Page Gestion de l'adaptateur  
 Utilisez la page Gestion de l'adaptateur pour spécifier la logique de gestion de conception de votre adaptateur.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Parcourir**|Sélectionner l'assembly qui implémente la logique de gestion de l'adaptateur de conception de votre adaptateur. Une liste des types publics exposés par cet assembly apparaît dans la liste déroulante. Dans cette liste déroulante, sélectionnez le type de l'assembly spécifié qui implémente la logique de gestion de l'adaptateur pour cet adaptateur.|  
  
### <a name="output-file-name"></a>Nom du fichier de sortie  
 Utilisez la page Nom du fichier de sortie pour spécifier un nom et un emplacement pour le fichier de sortie.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Parcourir**|Choisir un nom et un emplacement pour le fichier de sortie. Le registre de l'adaptateur est écrit dans ce fichier.|  
  
## <a name="remarks"></a>Notes  
 L'utilitaire Assistant Registre de l'adaptateur renseigne les propriétés du magasin de configuration du service d'authentification unique de l'entreprise avec des valeurs par défaut. Si votre adaptateur n'utilise pas les pages de propriétés standard fournies par l'infrastructure d'adaptateurs pour les propriétés d'adaptateur de gestionnaire et d'emplacement, vous devez modifier manuellement le fichier de Registre afin d'apporter des modifications à ces valeurs. Pour plus d’informations sur ces paramètres, consultez « Inscription de propriétés de l’adaptateur pour le magasin de configuration de l’authentification unique » dans la rubrique [inscription d’un adaptateur](../core/registering-an-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires dans le Kit de développement](../core/utilities-in-the-sdk.md)   
 [Inscription d’un adaptateur](../core/registering-an-adapter.md)