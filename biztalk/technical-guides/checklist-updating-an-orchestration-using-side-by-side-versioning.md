---
title: "Liste de vérification : Mise à jour d’une Orchestration à l’aide du contrôle de version côte à côte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97f66987-0269-4dfe-a648-7b68412e86fe
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 110eb0df6373d8679fed0431c91d10a6633e0610
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-updating-an-orchestration-using-side-by-side-versioning"></a>Liste de vérification : Mise à jour d’une Orchestration à l’aide du contrôle de version côte à côte
Modifications aux orchestrations peuvent être plus complexe que des modifications d’autres artefacts, tels que des cartes. Si vous avez des orchestrations de courte durée de vie, une mise à jour simple peut suffire. Mais si vous avez les orchestrations longues ou que vous ne peut pas terminer les instances existantes, le contrôle de version côte à côte sera la seule option.  
  
 Lorsqu’une orchestration gère des transactions à long terme, vous ne pouvez pas modifier immédiatement à la version mise à jour de l’orchestration. Vous devez autoriser la version d’origine terminer le traitement de ses messages afin qu’ils ne soient pas perdues. Pour ce faire, vous déployez l'orchestration mise à jour dans l'application utilisée par l'orchestration d'origine. Vous arrêtez ensuite la version d'origine et démarrez la version mise à jour afin qu'elle reçoive tous les nouveaux messages tandis que l'ancienne version continue de traiter les éventuels messages en vol. Une fois que l'orchestration d'origine a fini de traiter tous ses messages, vous annulez son déploiement dans l'application BizTalk dans laquelle elle a été déployée.  
  
|Étapes|Référence|  
|-----------|---------------|  
|Après avoir apporté les modifications nécessaires à l’orchestration, incrémentez le numéro de version d’assembly.|[Comment mettre à jour un Assembly](../technical-guides/how-to-update-an-assembly.md)|  
|Déployez l’assembly à partir de Visual Studio dans une application BizTalk, puis testez l’assembly. **Remarque :** veillez à sélectionner l’option de déploiement pour installer l’assembly dans le GAC.|[Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154719) (http://go.microsoft.com/fwlink/?LinkID=154719).|  
|Exportez l’assembly à partir de l’application dans votre environnement de test dans un fichier .msi.|[Comment exporter une Application vers un fichier .msi](../technical-guides/how-to-export-an-application-to-an-msi-file.md)|  
|Importer le fichier .msi dans l’application BizTalk dans votre environnement de production qui contient l’orchestration que vous souhaitez mettre à jour. **Remarque :** vous pouvez utiliser les étapes suivantes pour tester l’assembly, ainsi que de déployer dans votre environnement de production.|[Comment importer une Application à partir d’un fichier .msi](../technical-guides/how-to-import-an-application-from-an-msi-file.md)|  
|Lier l’orchestration mise à jour avec les mêmes liaisons que l’orchestration d’origine.|[Comment configurer des liaisons d’une Orchestration](http://go.microsoft.com/fwlink/?LinkId=154850) (http://go.microsoft.com/fwlink/?LinkId=154850).|  
|Désinscrivez l'orchestration d'origine, puis démarrez l'orchestration mise à jour. **Remarque :** pour éviter toute suppression de messages, vous devez le faire par programme.|Pour plus d’informations sur le déploiement de l’orchestration par programme, consultez [déploiement et démarrage d’une nouvelle Version d’une Orchestration par programme](http://go.microsoft.com/fwlink/?LinkId=154851) (http://go.microsoft.com/fwlink/?LinkId=154851).<br /><br /> Pour plus d’informations sur le déploiement de l’orchestration manuellement, consultez la rubrique suivante dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aider à :<br /><br /> -   [Comment désinscrire une Orchestration](http://go.microsoft.com/fwlink/?LinkId=154852) (http://go.microsoft.com/fwlink/?LinkId=154852).<br />-   [Comment inscrire une Orchestration](http://go.microsoft.com/fwlink/?LinkId=154853) (http://go.microsoft.com/fwlink/?LinkId=154853).<br />-   [Comment démarrer une Orchestration](http://go.microsoft.com/fwlink/?LinkId=154854) (http://go.microsoft.com/fwlink/?LinkId=154854).|  
|Surveillance du système pour les instances de la version d’orchestration d’origine à l’aide de concentrateur du groupe page Affichage de la requête.|[Comment afficher des informations sur l’Instance d’une Orchestration](http://go.microsoft.com/fwlink/?LinkId=154855) (http://go.microsoft.com/fwlink/?LinkId=154855).|  
|Lorsque toutes ses instances actives, mises en attente et suspendues sont terminées, annulez le déploiement de l’orchestration d’origine à partir de l’application.|[Comment supprimer une Orchestration à partir d’une Application](http://go.microsoft.com/fwlink/?LinkId=154856) (http://go.microsoft.com/fwlink/?LinkId=154856).|  
|Si vous le souhaitez désinstaller la version d’origine de l’assembly du GAC sur chaque ordinateur qui exécute l’application.|[Comment désinstaller un Assembly du GAC](http://go.microsoft.com/fwlink/?LinkId=154857) (http://go.microsoft.com/fwlink/?LinkId=154857).|  
  
## <a name="binding-to-receive-ports-and-locations"></a>Liaison de Ports et emplacements de réception  
 Si vous souhaitez créer de nouveaux ports et emplacements de la nouvelle version de l’orchestration de réception, simplement pour les nouveaux ports de liaison et les nouveaux artefacts de l’inscription/démarrage généralement seront suffisants. Création de nouveau des emplacements de réception et ports est généralement la meilleure approche, en particulier si votre scénario utilise les orchestrations longues où un certain nombre de corrélation reçoit toujours besoin d’être traités. Dans ce cas, vous ne pouvez peut-être pas réutiliser les ports de réception ou d’effectuer unenlistment. Si vous créez de nouveaux ports, veillez à ce qu’il est possible de vos systèmes back-end et partenaire gérer cette modification. Si ce n’est pas le cas, vous devez attendre que toutes les instances de longs déboucher sur avant la mise à niveau.  
  
 Si vous souhaitez utiliser des ports existants, procédez comme suit :  
  
1.  Lier la nouvelle version de l’orchestration aux ports existants.  
  
2.  Désinscrire (mais ne l’arrêtez pas) l’ancienne version de l’orchestration.  
  
3.  Inscrire et démarrer la nouvelle version de l’orchestration.  
  
    > [!NOTE]  
    >  Vous pouvez utiliser un script pour effectuer les étapes 2 et 3 dans une transaction afin que les messages ne sont pas absentes abonnements entre en cliquant sur manuel.