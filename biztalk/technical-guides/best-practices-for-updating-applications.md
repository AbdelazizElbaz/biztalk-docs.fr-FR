---
title: "Meilleures pratiques pour la mise à jour des Applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 072eaf25-a1ee-4af3-b034-525a04260ef4
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f17fd3ce03ab4c974bff1b5198d27385d311ed70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-updating-applications"></a>Meilleures pratiques pour la mise à jour des Applications
Cette rubrique décrit les meilleures pratiques que vous devez envisager d’utiliser lors de la mise à jour des applications et artefacts BizTalk.  
  
## <a name="versioning"></a>Contrôle de version  
 **Implémenter une stratégie de contrôle de version**  
  
-   Une stratégie de contrôle de version correcte est essentielle si les longues transactions sont utilisées ou de l’application BizTalk ne peut pas être arrêtée pour effectuer des mises à niveau ou des correctifs de bogues. Vous devez planifier la stratégie de contrôle de version de tous les artefacts BizTalk : schémas, mappages, des adaptateurs personnalisés, pipelines, les composants de pipeline, orchestrations, des règles d’entreprise, BAM et des classes personnalisées appelées dans les orchestrations et des mappages.  
  
 **Correspond à des assemblys dans la base de données de gestion BizTalk et le global assembly cache (GAC)**  
  
-   Assurez-vous que les mêmes versions des assemblys se trouvent dans la base de données de gestion BizTalk comme dans le GAC, afin que votre application fonctionne correctement. Si un assembly ne fait pas l'objet d'une installation systématique dans le GAC lors de son déploiement, il se peut que les versions contenues dans le GAC et dans la base de données de gestion BizTalk diffèrent, avec comme conséquence la génération d'erreurs lors de l'exécution.  
  
 **Utilisez l’outil Vérificateur d’Assembly BizTalk et le GAC à distance pour vérifier le contrôle de version**  
  
-   Le **outil Vérificateur d’Assembly BizTalk et à distance GAC** (BTSAssemblyChecker.exe) vérifie les versions des assemblys déployés dans la base de données de gestion BizTalk et vérifie qu’ils sont inscrits correctement dans le GAC sur tous les BizTalk Ordinateurs serveur. Vous pouvez utiliser cet outil pour vérifier que tous les assemblys contenant les artefacts d’une certaine application BizTalk sont installés sur tous les nœuds de BizTalk. L’outil est particulièrement utile en conjonction avec une stratégie de contrôle de version solide pour vérifier que la version correcte d’un jeu d’assemblys est installée sur chaque ordinateur BizTalk, en particulier lorsque l’approche de déploiement de côte à côte est utilisé.  
  
-   L’outil est disponible avec le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Support\Tools\x86\BTSAssemblyChecker.exe support d’installation.  
  
 **Utilisez un produit de contrôle de version**  
  
-   Vous devez utiliser un produit de contrôle de version, tel que Microsoft Visual Studio® Team Foundation Server 2010, les artefacts BizTalk le suivi et le contrôle de version. Pour plus d’informations sur Microsoft Visual Studio® Team Foundation Server 2010, consultez [Microsoft Visual Studio® Team Foundation Server 2010](http://go.microsoft.com/fwlink/?LinkId=210637) (http://go.microsoft.com/fwlink/?LinkId=210637)  
  
 **Artefacts de facteur dans plusieurs applications BizTalk**  
  
-   Pour pouvoir effectuer des artefacts BizTalk versioning des assemblys, vos assemblys de la solution BizTalk doivent factorisation (empaquetées) de manière à autoriser le contrôle de version de BizTalk Server. Pour plus d’informations sur la factorisation, consultez [Ajout d’artefacts à une Application](../technical-guides/adding-artifacts-to-an-application.md).  
  
## <a name="updating-an-application"></a>Mise à jour d’une Application  
 **Utilisez un fichier .msi pour mettre à jour d’une application**  
  
-   La mise à niveau des applications est généralement une opération délibérée et précise en production. Lorsque vous mettez à niveau une application, vous devez normalement utiliser une liste de contrôle manuel. Toutefois, vous pourrez peut-être simplifier certaines étapes à l’aide d’un fichier .msi. Lorsque vous utilisez un fichier .msi, vous pouvez encapsuler des artefacts de votre application dans un package distribuable. Un fichier .msi est particulièrement utile lorsque vous déployez dll mis à jour sur plusieurs zones du runtime ou effectuez un déploiement au niveau du groupe. Lorsque vous créez un fichier .msi, vous devez exclure tous les autres ressources inchangées et les liaisons à partir du package.  
  
-   Si vous mettez à jour un assembly BizTalk, vous devez arrêter, désinscrire, inscrire de nouveau et puis démarrez manuellement les artefacts BizTalk avant et après avoir importé et installer le fichier .msi. Pour plus d’informations sur la mise à jour d’un assembly BizTalk, consultez [liste de vérification : mise à jour d’un Assembly](../technical-guides/checklist-updating-an-assembly.md).  
  
-   Si vous mettez à niveau un assembly BizTalk Server à l’aide du contrôle de version côte à côte, vous devez effectuer les étapes manuelles avant et après l’utilisation du fichier .msi. Pour plus d’informations sur les étapes manuelles nécessaires, consultez [liste de vérification : mise à jour d’un contrôle de version côte à côte à l’aide de l’Application](../technical-guides/checklist-updating-an-application-using-side-by-side-versioning.md).  
  
## <a name="updating-an-assembly"></a>Mise à jour d’un Assembly  
 **Incrémenter la version d’un assembly dans un environnement de production**  
  
-   Si vous mettez à jour un assembly qui s'exécute dans un environnement de production, vous devez toujours augmenter le numéro de version de l'assembly d'un incrément.  
  
 **Mettre à jour le GAC avec un assembly mis à jour**  
  
-   Lorsque vous mettez à jour un assembly contenant une orchestration, un schéma ou une carte, vous devez mettre à jour le GAC à l’assembly qui contient la nouvelle version. Sinon, BizTalk Server utilise la version obsolète. Pour ce faire, sur chaque ordinateur exécutant une instance de l'hôte auquel une application est liée, désinstallez, dans le GAC, l'ancienne version de l'assembly contenant l'artefact mis à jour et assurez-vous que la nouvelle version est installée.  
  
 **Redémarrer une instance d’hôte après la mise à jour d’un assembly**  
  
-   Si un assembly BizTalk dans une application existante est mise à jour, vous devrez peut-être redémarrer les instances d’hôte pour que les modifications prennent effet. Le redémarrage d’une instance d’hôte arrête toutes les autres applications qui sont exécutent sur l’instance d’hôte.  
  
## <a name="updating-an-artifact"></a>Mise à jour d’un artefact  
 **Annuler le déploiement d’un artefact dépendant avant l’artefact dont il dépend**  
  
-   Si vous annulez le déploiement d’un artefact dont dépend un autre artefact, vous devez tout d’abord annuler le déploiement l’artefact dépendant.  
  
    > [!NOTE]  
    >  Si vous ne pas annuler le déploiement de l’artefact dépendant tout d’abord, la console Administration de BizTalk Server s’affiche un avertissement et vous empêcher d’annulation du déploiement des artefacts dans un ordre incorrect.  
  
 **N’arrêtez pas un artefact dont dépend une autre application**  
  
-   Si vous arrêtez un artefact dans une application (qui peut être dû à l'arrêt de l'ensemble de l'application) dont une autre application dépend, l'application dépendante ne fonctionne pas correctement. Pour plus d’informations sur l’arrêt d’une application, consultez [comment démarrer et arrêter une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154729) (http://go.microsoft.com/fwlink/?LinkID=154729).  
  
 **Ajoutez une référence à un assembly avant de déplacer un artefact**  
  
-   Lorsque vous déplacez un artefact vers une nouvelle application, les autres artefacts dont il dépend sont également déplacés, sauf si la nouvelle application comporte une référence aux applications contenant les artefacts dont celui déplacé dépend. Les artefacts qui dépendent de celui déplacé sont également déplacés, sauf si les applications les contenant comportent une référence à la nouvelle application. Lorsque vous déplacez un artefact, la liste des autres artefacts seront également déplacés sont affichés.  
  
## <a name="updating-bindings"></a>Mise à jour des liaisons  
 **Automatiser la reconfiguration des liaisons**  
  
-   Lorsque vous mettez à jour un assembly dans une application, ses liaisons sont généralement remplacées, faute de quoi l'assembly risque de ne pas être lié, vous obligeant à une reconfiguration manuelle des liaisons. Vous pouvez automatiser ce processus à l’aide d’un fichier de liaison. Si vous mettez à jour la même version d’un assembly, vous pouvez tout d’abord exporter un fichier de liaison pour l’assembly, puis mettre à jour de l’assembly, puis importer l’assembly dans l’application et réappliquez les liaisons précédentes en important le fichier de liaison. Si vous mettez à jour un assembly avec une version plus récente, vous pouvez exporter un fichier de liaison, modifiez le fichier pour refléter la nouvelle version de l’assembly, importer le nouvel assembly dans l’application, puis appliquer les nouvelles liaisons en important le fichier de liaison. Pour plus d’informations sur les fichiers de liaison, consultez [comment exporter les liaisons pour un fichier de liaison](../technical-guides/how-to-export-bindings-to-a-binding-file.md). Pour plus d’informations sur la modification d’un fichier de liaison, consultez [personnalisation des fichiers de liaison](http://go.microsoft.com/fwlink/?LinkID=155000) (http://go.microsoft.com/fwlink/?LinkID=155000).  
  
## <a name="starting-or-stopping-an-application"></a>Démarrer ou arrêter une Application  
 **Arrêter une application pour mettre à jour des artefacts**  
  
-   Si vous n’arrêtez pas d’une application pour mettre à jour des artefacts de l’application, vous devez arrêter la publication pour la base de données MessageBox en désactivant les points de terminaison, temporairement, arrêter et désinscrire toutes les instances en cours d’exécution. Pour arrêter et désinscrire des instances en cours d’exécution, toutes les instances mises en attente ou suspendues doivent être manuellement repris et s’est terminées ou arrêtées.  
  
-   Bien que cela ne soit pas obligatoire, nous vous recommandons d'arrêter les applications lorsque vous mettez à jour un artefact ou installez une autre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment exporter des liaisons vers un fichier de liaison](../technical-guides/how-to-export-bindings-to-a-binding-file.md)