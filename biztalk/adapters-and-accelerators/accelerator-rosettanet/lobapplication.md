---
title: LOBApplication | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trading partners, submitting actions
- LOBs, submitting actions
- LOBApplication utility
- trading partners, response messages
- LOBs, LOBApplication utility
- LOBs, response messages
ms.assetid: ad5986af-4175-49cd-806b-04e1fde63f55
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af11e69c90c9d211e36e706710c1d1de44a72399
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="lobapplication"></a>LOBApplication
Vous utilisez l’utilitaire LOBApplication pour envoyer un message d’action ou d’une réponse à un partenaire commercial, en simulant un programme de bureau de métier (LOB) réels.  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] fournit des exemples de messages dans la \< *lecteur*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\ SampleInstances dossier.  
  
## <a name="location-in-sdk"></a>Emplacement dans le kit de développement logiciel (SDK)  
 \<*lecteur*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication  
  
## <a name="running-lobapplication"></a>LOBApplication en cours d’exécution  
  
#### <a name="to-run-lobapplication"></a>Pour exécuter LOBApplication  
  
1.  Dans l’Explorateur Windows, accédez à \< *lecteur*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\\.  
  
2.  Double-cliquez sur **LOBApplication.exe**, puis appuyez sur ENTRÉE.  
  
     Les pages qui suivent vous invitent à entrer les informations requises pour exécuter l’utilitaire.  
  
## <a name="syntax-for-lobapplication"></a>Syntaxe de LOBApplication  
 Utilisez le **Proxy d’Application LOB** page pour spécifier les noms de page d’accueil et les partenaires, les propriétés de processus PIP (Partner Interface) et les propriétés de message pour le message envoyé par l’utilitaire LOBApplication.  
  
 Le tableau suivant décrit l’utilisation de chaque champ sur la **Proxy d’Application LOB** page.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Nom du profil de base**|Tapez le nom de l’organisation d’origine (tiers de la source).|  
|**Nom du partenaire commercial**|Tapez le nom du partenaire commercial (tiers de destination).|  
|**Nom du PIP**|Tapez le code de l’affichage du PIP, par exemple, type **3A2**. Cette valeur respecte la casse.|  
|**Version PIP**|Type de la version du PIP, par exemple, type **V02.00**. Cette valeur respecte la casse.|  
|**ID d’Instance PIP** (facultatif)|Tapez un ID d’instance alphanumériques pour le PIP, par exemple, tapez **STD_3A2_V02.02**. Évitez les caractères spéciaux. L’ID doit être unique par partenaire et par code PIP. Pour les messages qui sont marqués comme messages d’action, si l’ID d’Instance est vide, l’utilitaire LOBApplication utilise une valeur HUID générée pour l’ID d’Instance PIP. **Remarque :** lorsque vous sélectionnez **réponse** dans les **Message catégorie**, vous devez taper l’ID d’Instance PIP dans ce champ.|  
|**Nom de fichier**|Cliquez sur le bouton de sélection (...), accédez au dossier qui contient le fichier d’instance PIP, puis cliquez sur le fichier d’instance PIP.|  
|**Catégorie de message**|Sélectionnez le type de message (**Action** ou **réponse**).|  
|**Pièces jointes**|Cliquez sur **ajouter**, accédez au dossier qui contient le fichier de pièce jointe, puis cliquez sur **ouvrir**.|  
|**Envoyer le Message**|Cliquez ici pour envoyer le message.|  
|**État**|Lire l’état de l’action dans ce champ.|  
  
## <a name="remarks"></a>Notes  
 L’utilitaire LOBApplication crée un message avec les propriétés spécifiées et l’envoie au partenaire commercial. Cet utilitaire écrit les données de contenu de service dans le message à la base de données BTARNDATA, dans la table MessageFromLOB. Il simule l’envoi d’un message d’action.  
  
 Les exemples de messages dans le dossier SampleInstances sous le dossier LOBApplication dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK sont préconfigurés à assumer les identificateurs d’entreprise Global (GBIs) suivants : 123456789 pour l’organisation d’origine et 987654321 pour le partenaire organisation. Vous devez modifier les exemples de messages dans un éditeur de texte à utiliser d’autres GBIs.  
  
 Vous utilisez l’utilitaire LOBApplication pour simuler un programme de bureau métier-envoi d’un message. Vous utilisez l’utilitaire LOBWebApplication pour simuler une application Web de métier-envoi d’un message.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [LOBWebApplication](../../adapters-and-accelerators/accelerator-rosettanet/lobwebapplication.md)