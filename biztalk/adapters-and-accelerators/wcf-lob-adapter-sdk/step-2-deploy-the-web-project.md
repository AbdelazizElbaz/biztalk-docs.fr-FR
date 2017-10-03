---
title: "Étape 2 : Déployer le projet Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb775a89-2e2d-43e5-94ae-f75c1756dbd7
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 503ce37fd06f91d5036f08c9eee752017c0ad21c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-deploy-the-web-project"></a>Étape 2 : Déployer le projet Web
![Étape 2 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **Durée :** 5 minutes  
  
 Dans cette étape, vous allez publier le projet Web généré dans [étape 1 : utiliser l’Assistant développement d’adaptateurs pour créer le projet Web](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md) pour Internet Information Services (IIS).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette étape, vous devez avoir terminé [étape 1 : utiliser l’Assistant développement d’adaptateurs pour créer le projet Web](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md). Votre serveur Web doit avoir également un certificat SSL installé pour permettre une communication HTTPS.  
  
### <a name="to-compile-and-deploy-the-web-project"></a>Pour compiler et déployer le projet Web  
  
1.  Dans [!INCLUDE[vs2010](../../includes/vs2010-md.md)], charger le projet EchoWeb créé précédemment.  
  
2.  Ouvrir un [!INCLUDE[vs2010](../../includes/vs2010-md.md)] invite de commandes.  
  
3.  À l’invite de commandes, à partir du dossier C:\tutorials\echoweb, tapez la commande suivante et appuyez sur ENTRÉE :  
  
     **sn /k EchoWebKey.snk**  
  
     Un message de confirmation, **écrites dans EchoWebKey.snk de paire de clés**, affiche sur la ligne de commande.  
  
4.  Fermez l'invite de commande.  
  
5.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet EchoWeb, puis sélectionnez **publier le Site Web**.  
  
6.  Dans le **publier le Site Web** boîte de dialogue, pour **emplacement cible**, entrez **http://machinename/EchoWeb**. Sélectionnez **autoriser ce site précompilé à être mis à jour**, **utiliser fixe pour les assemblys d’affectation de noms et une page**, et **activer de noms forts sur les assemblys précompilés**. Dans le **emplacement du fichier de clé** , cliquez sur le bouton de sélection **(...)**  bouton, sélectionnez le fichier EchoWebKey.snk créé précédemment, puis cliquez sur **OK**.  
  
7.  Pour vérifier que le site Web a été correctement créé, démarrez Internet Explorer, entrez **lien hypertexte « http://localhost/EchoWeb/EchoOutboundContract.svc » http://localhost/EchoWeb/EchoOutboundContract.svc** dans la barre d’adresses, et Appuyez sur ENTRÉE. Une page Web qui décrit le EchoOutboundContractClient doit apparaître.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Vous venez de publier votre projet Web pour IIS.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez compilé et déployé le projet, vous pouvez passer à [étape 3 : créer un fichier de définition d’Application](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 3 : Hébergeant l’adaptateur de l’écho dans IIS](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)