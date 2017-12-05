---
title: "Étape 2 : Mettre à jour et déployer la Solution du didacticiel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d03adfdd-1160-4e8c-a564-3acb2ecd0476
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67fd3d34f25dd409121a3a21c9eb419b4aadce6e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-update-and-deploy-the-tutorial-solution"></a>Étape 2 : Mettre à jour et déployer la Solution du didacticiel
![Étape 2 sur 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")  
  
 Au cours de cette étape, vous allez mettre à jour la solution fournie pour ce didacticiel, puis générer et déployer l'assembly du didacticiel. Les éléments nécessaires à ce didacticiel (schéma, pipeline d'envoi personnalisé et mappage) ont déjà été créés. Le mappage permet de convertir les données EDI 850 au format requis par votre système de commande.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-enable-the-edi-inbound-processing-solution-to-be-built-in-visual-studio"></a>Pour activer la génération de la solution EDI Inbound Processing dans Visual Studio  
  
1.  Démarrer **Microsoft Visual Studio** en tant qu’administrateur.  
  
    > [!CAUTION]
    >  Si vous ne démarrez pas Visual Studio avec des privilèges d'administrateur, une erreur est générée lors du déploiement de la solution vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Dans Visual Studio, cliquez sur **fichier**, pointez sur **ouvrir**, puis cliquez sur **projet/Solution**. Déplacer vers [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial, sélectionnez **EDI Inbound Processing.sln**, puis cliquez sur **ouvrir**.  
  
    > [!NOTE]
    >  Cette rubrique part du principe que vous avez déjà ajouté une référence de votre application à l'application BizTalk EDI, qui contient les schémas, pipelines et orchestrations EDI. Dans le cas contraire, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
3.  Cliquez sur le **Inbound_EDI** de projet dans l’Explorateur de solutions, puis sélectionnez **propriétés**.  
  
4.  Dans l’arborescence de la **les Pages de propriétés de Inbound_EDI** boîte de dialogue, sélectionnez **déploiement** et dans le **Server** champ vous assurer que le nom de votre ordinateur est entré.  
  
5.  Dans l’arborescence de la console, cliquez sur **signature** , puis sélectionnez **signer l’assembly**. Pour **choisir un fichier de nom fort de la clé**, sélectionnez \< **nouveau...**  \> et entrez **keyfile.snk** comme le **nom de fichier de clé**. Désactivez **protéger mon fichier de clé avec un mot de passe** puis cliquez sur **OK**.  
  
6.  Fermer le **les Pages de propriétés de Inbound_EDI** boîte de dialogue.  
  
### <a name="to-deploy-the-project"></a>Pour déployer le projet  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur le **X12_00401_850.xsd** schéma. Vérifiez qu'il est ouvert.  
  
2.  Dans l’Explorateur de solutions, double-cliquez sur le **Inbound4010850_to_OrderFile.btm** carte. Vérifiez qu'il est ouvert.  
  
    > [!NOTE]
    >  Le mappage Inbound4010850_to_OrderFile.btm du projet mappe les données du message test 850 entrant au fichier XML sortant placé dans le dossier OrderSystem (\toOrderSystem).  
  
3.  Dans l’Explorateur de solutions, cliquez sur le **Inbound_EDI** de projet et sélectionnez **générer** pour générer le projet.  
  
4.  Dans l’Explorateur de solutions, cliquez sur le **Inbound_EDI** de projet et sélectionnez **déployer** pour déployer le projet.  
  
5.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, \<  **Tous les artefacts** \> , puis sélectionnez **ressources**. Vérifiez que le **Inbound_EDI** assembly est répertorié.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous configurez un profil de tiers et d’entreprise pour votre organisation (**OrderSystem**), comme décrit dans [étape 3 : configurer un tiers et un profil d’entreprise pour votre organisation](../core/step-3-configure-a-party-and-business-profile-for-your-organization1.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Préparer le didacticiel pour développeur d’interface EDI](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)