---
title: "Génération et publication de formulaires MT-MX sur le Site SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4adf7117-11ad-4a8e-8d6a-fd78c5e496a3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e2bd45c54bfc312a52d199a2f117a108207cdf5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generating-and-publishing-mtmx-forms-on-the-sharepoint-site"></a>Génération et publication de formulaires MT/MX sur le Site SharePoint
**Pour générer et publier des formulaires MT/MX sur un site SharePoint :**  
  
1.  Télécharger l’utilitaire Générateur de formulaire et l’enregistrer localement sur l’ordinateur.  
  
2.  Ouvrez le **FormGenerator.sln** à partir du dossier téléchargé ci-dessus et de compiler la solution.  
  
3.  À l’invite de commandes, accéder au dossier de l’exécutable compilé (FormGenerator.exe). Par exemple, si vous avez créé l’utilitaire en mode débogage, accéder à la **... \bin\Debug** dossier.  
  
4.  Tapez FormGenerator.exe [-b] [-\<non. des chemins d’accès du dossier de modèle >]  
  
     `<TemplateFolderPath> <DestinationFolderPath> <DocumentSchemaLocation> {[<SpaceSeparatedDocumentSchemaList>] | [-f <NameOfFileContainingSchemaList>]}`. Remplacez les paramètres avec les noms de dossier nouvellement créé.  
  
5.  La commande ci-dessus génère également le schéma d’enveloppe à MX message réparation.  
  
6.  Accédez au dossier de sortie \<DestinationFolderPath >. Dans \<DestinationFolderPath >, ouvrez le dossier du modèle de formulaire InfoPath pour lequel vous souhaitez générer le formulaire. Par exemple, si vous souhaitez générer le formulaire InfoPath de MT103, ouvrez le dossier MT103 à la DestinationFolderPath et ouvrez le TemplateDS.sln.  
  
7.  Dans l’Explorateur de solutions, double-cliquez sur le **manifest.xsf**. Il ouvre le fichier de la conception du formulaire InfoPath qui prend un certain temps à obtenir ouvert.  
  
    > [!NOTE]
    >  MX messages manifest.xsf peut prendre 2 à 5 minutes obtenir ouvert.  
  
8.  Dans manifest.xsf, accédez à **Outils -> Options de formulaire - > sécurité et approbation** option de menu. Vérifiez le **confiance totale** option doit être activée pour l’autorisation.  
  
9. Sélectionnez le **signer ce modèle de formulaire** case à cocher. Cliquez sur **sélectionner un certificat**. Dans ce cas, sélectionnez le certificat avec lequel vous souhaitez signer le formulaire. Cliquez sur **OK**.  
  
10. Enregistrer **manifest.xsf**.  
  
11. Accédez à **Affichage -> tâches de conception**. Dans le volet de tâches de conception, cliquez sur **publier un modèle de formulaire** option.  
  
12. Dans la fenêtre de l’Assistant Publication, sélectionnez **vers un emplacement réseau** et cliquez sur **suivant**.  
  
13. Dans le formulaire modèle chemin d’accès et le fichier de zone de texte Nom, tapez **http://localhost/sites/BASSite/Templates/\<MessageType > .xsn** et type  **\<MessageType >** sous la forme Zone de texte Nom du modèle et cliquez sur **suivant**.  
  
14. Cliquez sur **Suivant**.  
  
15. Cliquez sur **publier et fermer**.  
  
16. Dans Internet Explorer, ouvrez votre site SharePoint **http://localhost/sites/bassite/templates**.  
  
17. Pointez sur  **\<MessageType >**et cliquez sur la flèche bas en regard de celui-ci, puis cliquez sur **modifier les propriétés de**.  
  
18. Dans les modèles :\< MessageType > fenêtre, dans la zone de Namespace :  
  
    -   Si vous générez des formulaires InfoPath de MT, tapez : **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMTxxx**  
  
    -   Si vous générez des formulaires InfoPath de MX, tapez : **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX _\<MessageName >**  
  
         Cela permet d’identifier l’instance de message par le modèle correspondant.  
  
19. Cliquez sur **enregistrer et fermer**.