---
title: Outil de nettoyage A4SWIFT | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: A4SWIFT Cleanup tool
ms.assetid: e694f824-6097-4d60-bc7b-b4f1a40acea0
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b2d0e251bf5e8a4169ff0d86cc6635944ca12e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="a4swift-cleanup-tool"></a>Outil de nettoyage A4SWIFT
Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] outil de nettoyage vous permet de préparer un serveur qui a le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] installé dessus pour une nouvelle installation de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]. L’outil supprime les artefacts de A4SWIFT, tels que les contrats, les services et les stratégies du moteur de règles d’entreprise (BRE) et annule le déploiement des assemblys. Exécution de l’outil vous permet d’éviter la suppression manuelle de nombreux artefacts A4SWIFT et résout les problèmes d’annulation du déploiement des assemblys qui peuvent être référencées à partir d’autres assemblys.  
  
 Lorsque vous exécutez l’outil de nettoyage, vous avez le choix de laisser A4SWIFT installé sur l’ordinateur (par défaut), ou A4SWIFT désinstallation après avoir supprimé les artefacts. Vous devez exécuter l’outil avant de désinstaller A4SWIFT.  
  
> [!CAUTION]
>  N’utilisez pas l’outil de nettoyage A4SWIFT dans un environnement de production. L’outil est destiné à être utilisée dans un environnement de développement de serveur unique, pas dans un déploiement multiserveur.  
  
> [!NOTE]
>  Par défaut, l’outil de nettoyage ne fonctionne pas pour une autre langue que l’anglais. Toutefois, vous pouvez modifier l’environnement afin que l’outil de nettoyage fonctionne sur un ordinateur localisé. Exécutez l’outil de FormPublish avec le paramètre t et la chaîne localisée pour la bibliothèque de documents modèles, par exemple, **t:VorLagen** dans un environnement en allemand. Vous pouvez ensuite exécuter l’outil de nettoyage dans un environnement localisé.  
  
 Les éléments suivants doivent être remplis pour l’outil de nettoyage à exécuter :  
  
-   Vous devez être membre du [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupes d’administrateurs.  
  
-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]doit être installé sur le serveur sur lequel vous exécutez l’outil.  
  
-   MrsrConfiguration.dll, Shared.dll et RuleEngineExtension.dll doivent être déployés sur le serveur sur lequel vous exécutez l’outil.  
  
## <a name="what-the-cleanup-tool-does"></a>Ce que fait l’outil de nettoyage  
 L’outil de nettoyage A4SWIFT effectue les opérations suivantes :  
  
-   S’exécute **annuler le déploiement de BM** contre ForActivities.xml et MRSRBAM.xml  
  
-   Supprime les fichiers FrrActivities_ConnectionStrings.xml et MRSRActivities_ConnectionStrings.xml, s’ils existent  
  
-   Supprime les 2.1 A4SWIFT s’il existe (si vous avez mis à niveau le serveur à [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], mais le programme d’installation n’a pas A4SWIFT 2.1 est installé) et supprime le dossier A4SWIFT 2.1  
  
-   Annule le déploiement de tous les assemblys A4SWIFT  
  
-   Supprime le groupe administrateur de A4SWIFT et le groupe utilisateurs d’A4SWIFT  
  
-   Supprime la base de données A4SWIFT  
  
-   Supprime le répertoire virtuel A4SWIFT  
  
-   Exécute une désinstallation sans assistance complète de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] et supprime la [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] dossier (si)  
  
 Supprime les artefacts et annule le déploiement des assemblys, l’outil de nettoyage effectue également les opérations suivantes :  
  
-   Démarre le Service d’administration Internet Information Services (IIS) pour pouvoir s’exécuter  
  
-   Arrête et redémarre les services MSSQLSERVER, SQLSERVERAGENT, BizTalk et Enterprise Single Sign-On  
  
#### <a name="to-run-the-a4swift-cleanup-tool"></a>Pour exécuter l’outil de nettoyage A4SWIFT  
  
1.  Avant d’exécuter l’outil de nettoyage A4SWIFT, annuler le déploiement d’un projet qui fait référence à des assemblys par défaut A4SWIFT.  
  
2.  Ouvrez une invite de commandes et la déplacer vers \< *lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tools.  
  
3.  Type **A4SWIFTCleanupTool.exe** , puis appuyez sur **entrée**.  
  
    > [!NOTE]
    >  Lorsque vous exécutez initialement A4SWIFTCleanupTool.exe, l’outil affiche un écran d’aide et vous invite à entrer un paramètre. L’outil ne s’exécutera pas jusqu'à ce que vous entrez le paramètre.  
  
4.  Selon les actions que vous souhaitez que l’outil prenne, appuyez sur une des clés suivantes, puis appuyez sur **entrée**:  
  
    -   **0** pour aucune action effectuée (par défaut)  
  
    -   **1** pour supprimer toutes les ressources A4SWIFT locales sur l’ordinateur, y compris les paramètres de répertoire et Registre virtuels  
  
    -   **2** pour supprimer toutes les ressources A4SWIFT partagées sur le groupe BizTalk Server, y compris les dossiers Sharepoint Web, les modèles de message FIN, les stratégies BRE vocabulaires, artefacts BizTalk et la base de données A4SWIFT  
  
    -   **3** pour supprimer toutes les ressources locales et partagées  
  
    -   **4** pour supprimer toutes les ressources locales et partagés et désinstaller le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils](../../adapters-and-accelerators/accelerator-swift/tools.md)