---
title: "Étape 1 : Préparer le didacticiel pour développeur d’Interface EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9be1bddf-d673-4054-87f5-0205b8b5cc0d
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b222e425f44e58d79ab65d848a7aff395b1284b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-prepare-for-the-edi-interface-developer-tutorial"></a>Étape 1 : Préparer le didacticiel pour développeur d’Interface EDI
![Étape 1 sur 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-1of9.gif "Step_1of9")  
  
 Le didacticiel pour développeur d'interface EDI est exécuté sur un seul ordinateur. Pour préparer le didacticiel, vous devez installer et configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme décrit dans [vue d’ensemble de l’Installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5). Vous devez également ajouter une référence à l'application EDI BizTalk  
  
> [!NOTE]
>  Pour ce didacticiel fonctionne, il doit être exécuté sur une plateforme à l’aide d’IIS 7.5 ou IIS 8.  
  
 Les fichiers requis pour le didacticiel pour développeur d'interface EDI sont situés dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial. Les dossiers et fichiers requis pour le didacticiel sont les suivants :  
  
|Dossier\Fichier|Fonction|  
|------------------|-------------|  
|\SDK\EDI Interface Developer Tutorial\EDI Inbound Processing.sln|Fichier de solution que vous utilisez dans Visual Studio pour créer ce scénario de messagerie.|  
|\SDK\EDI Interface Developer Tutorial\keyfile.snk|Fichier de clé d'assembly spécifié pour le fichier de la solution.|  
|\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\SamplePO.txt|Exemple de fichier de message (version 4010 850) utilisé pour tester la solution.|  
|\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\Inbound4010850_to_OrderFile.btm|Mappage BizTalk qui convertit les données du message 850 au format requis par le système de commande.|  
|\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\SendOrderFilePipeline.btp|Pipeline d'envoi qui traite l'envoi du message de test vers le système de commande.|  
|\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\X12_00401_850.xsd|Schéma 850 pour le message de test.|  
\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\fromTHEM|Dossier de réception du message 850 entrant provenant de Fabrikam.|  
|\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\toOrderSystem|Dossier vers lequel le message 850 sortant est envoyé, qui représente l'application principale du système de commande.|  
|\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\toTHEM_997|Dossier vers lequel les accusés de réception 997 sont envoyés, qui représente Fabrikan.|  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-add-reference-to-the-biztalk-edi-application"></a>Pour ajouter une référence à l’Application EDI BizTalk  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la Console, sous le **Applications** nœud, cliquez sur l’application que vous souhaitez utiliser pour EDI, telles que BizTalk Application 1. Pointez sur **ajouter**, puis cliquez sur Références.  
  
2.  Dans le **ajouter une référence d’Application** boîte de dialogue, sélectionnez **Application EDI BizTalk**, puis cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous générez et déployez l’assembly Inbound_EDI, comme décrit dans [étape 2 : mettre à jour et déployer la Solution du didacticiel](../core/step-2-update-and-deploy-the-tutorial-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 2 : EDI Interface Developer Tutorial.](../core/tutorial-2-edi-interface-developer-tutorial.md)