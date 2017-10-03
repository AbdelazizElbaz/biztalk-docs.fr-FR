---
title: "Comment exécuter l’Assistant Configuration du Port | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Port Configuration Wizard [Orchestration Designer], starting
- Port Configuration Wizard [Orchestration Designer], how to
- Port Configuration Wizard [Orchestration Designer], about Port Configuration Wizard
- ports, Port Configuration Wizard [Orchestration Designer]
- Port Configuration Wizard [Orchestration Designer]
ms.assetid: 8035ce32-5ed4-49cb-b6f0-998b0460751e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbdb5843eb8011478f13c0de6443bb1ded177378
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-run-the-port-configuration-wizard"></a>Exécution de l'Assistant Configuration du port
Utilisez l'Assistant Configuration du port pour créer et configurer un port dans le Concepteur d'orchestration. Un port doit être associé à un type de port et vous utilisez l'Assistant pour sélectionner un type de port existant ou pour créer un type de port. Pour plus d’informations sur les ports et les types de ports, consultez [à l’aide des Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md).  
  
### <a name="to-start-the-wizard"></a>Pour démarrer l'Assistant  
  
1.  Clic droit sur un port (sur l’aire de conception ou dans la fenêtre Vue Orchestration), puis en cliquant sur **configurer le Port**.  
  
2.  Exécutez les éléments de balises actives dont les actions associées provoquent la création d'un port.  
  
3.  En sélectionnant le **nouveau paramètre de Port configuré** commande dans le menu contextuel du dossier Paramètres d’Orchestration dans la fenêtre Vue Orchestration.  
  
### <a name="to-run-the-wizard"></a>Pour exécuter l'Assistant  
  
1.  Ouvrez l'Assistant Configuration du port.  
  
2.  Spécifiez l'information de port. Pour vous faciliter la tâche, l'Assistant affiche plusieurs pages. À l’issue de chaque page, déplacer à la suivante en cliquant sur **suivant**, ou les déplacer vers le précédent en cliquant sur **précédent**.  
  
    -   **Propriétés du port**. entrez le nom du port.  
  
    -   **Sélectionnez un Type de Port.** Dans cette page, vous indiquez tout d’abord si vous souhaitez un **nouveau Type de Port** ou **Type de Port existant**. Si vous sélectionnez **Type de Port existant**, vous utilisez ensuite un contrôle d’arborescence pour choisir le type de port existant affecter.  
  
         Si vous sélectionnez **nouveau Type de Port**, vous devez entrer le nom du type de port dans le **nom** texte zone, ou acceptez le nom proposé par défaut. Vous sélectionnez également le modèle de communication du type de port (unidirectionnel ou requête-réponse) et les éventuelles restrictions d'accès à imposer sur le nouveau type de port.  
  
    -   **Liaison de port**. Dans cette page vous spécifiez la direction de communication, également connu sous le *polarité*et le type de liaison du port.  
  
         Le choix de polarité que vous effectuez dépend en partie du modèle de communication du type de port que vous avez sélectionné sur la page précédente de l’Assistant, **sélectionner un Type de Port**. Les choix que vous avez effectués sont résumés dans le tableau ci-dessous :  
  
        |Direction du port|Modèle de communication|Direction de communication à choisir dans la page Liaison de port|  
        |--------------------|---------------------------|---------------------------------------------------------------|  
        |Send|Unidirectionnel|Toujours envoyer les messages sur ce port.|  
        |Recevoir|Unidirectionnel|Toujours recevoir les messages sur ce port.|  
        |Envoi-Réception|Sollicitation-réponse|J’ai sera envoyer une requête et recevoir une réponse.|  
        |Réception-envoi|Requête-réponse|Recevoir une requête et envoyer une réponse.|  
  
         Vous avez le choix entre quatre types de liaison différents : spécifier plus tard, spécifier maintenant, dynamique et Direct. Chaque choix affiche un ensemble différent d'options de configuration, comme cela est résumé ci-dessous :  
  
         **Spécifier plus tard.** : après avoir sélectionné cette option, vous n'effectuez aucune autre sélection de configuration dans l'Assistant, car les informations de liaison ne sont pas déterminées au moment de la conception. Généralement, ces informations sont ajoutées par un administrateur lors du déploiement.  
  
         **Spécifier maintenant.** : lors de la conception, vous pouvez spécifier un URI définissant l'entité à laquelle le port doit être lié. Vous devez également effectuer une sélection dans une liste de types de transports qui inclut des options telles que Message Queuing BizTalk, FILE, SMTP, HTTP et SOAP. Il s'agit d'une liste codée en dur à des fins de liaison anticipée dans le concepteur d'orchestration, par conséquent, les autres transports ne sont pas disponibles dans cette liste. Enfin, vous sélectionnez un pipeline de réception et un pipeline d'envoi dans une liste des pipelines disponibles. La liste de chaque inclut tous les pipelines du projet actuel plus la possibilité de sélectionner un pipeline à partir d’un assembly référencé, qui affiche le **sélectionner le Type d’artefact** boîte de dialogue.  
  
         **Dynamique.** Cette option offre des choix similaires à **spécifier maintenant**, mais il est disponible uniquement pour un port d’envoi. Vous pouvez spécifier un pipeline d'envoi à utiliser. Vous pouvez spécifier le port séparément dans une **Expression** forme afin qu’il soit affecté au moment de l’exécution.  
  
         **Direct.** pour la liaison directe, vous pouvez soit sélectionner un port avec lequel établir la connexion, en vue d'effectuer un routage basé sur des expressions de filtre sur des messages entrants dans la base de données MessageBox, soit faire de ce port un port d'autocorrélation. Vous pouvez sélectionner un port dans une liste déroulante.  
  
         Pour plus d’informations, consultez [liaisons de Port](../core/port-bindings.md).  
  
3.  Terminez l'Assistant. La dernière page de l’Assistant Configuration du Port, intitulée **fin de l’Assistant Port**, affiche les choix effectués dans les pages précédentes afin que vous puissiez les vérifier avant de valider les modifications. Si les modifications sont correctes, cliquez sur **Terminer**. Sinon, cliquez sur **précédent** entrer à nouveau toutes les informations que vous souhaitez modifier. Déplacer à nouveau l’Assistant, puis cliquez sur **Terminer** lorsque les informations affichées dans la dernière page correspondent aux modifications que vous souhaitez rendre.  
  
    > [!NOTE]
    >  Si vous créez un nouveau port et que vous cliquez sur **Annuler** dans l’Assistant à tout moment avant la configuration de port de fin, le port n’est pas créé. Si vous avez utilisé l'Assistant pour modifier un port existant, annuler l'Assistant annule toutes les modifications que vous avez apportées. Sinon, si vous cliquez sur **Annuler** dans l’Assistant, l’adaptateur est créé, mais ses propriétés ne sont pas définies. Vous pouvez définir manuellement des propriétés de port dans la fenêtre Propriétés ou exécuter de nouveau l'Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation de Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md)