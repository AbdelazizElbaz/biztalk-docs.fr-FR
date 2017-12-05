---
title: Meilleures pratiques pour la surveillance | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5b180e2-bdd3-4081-9531-d96be7dabe1a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51b3d4761c32123db53ea35daf91d0f13d9a2488
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="best-practices-for-monitoring"></a>Meilleures pratiques pour l’analyse
Cette rubrique fournit les meilleures pratiques pour la surveillance de votre environnement Microsoft BizTalk Server et les applications.  
  
 **Créer et implémentez un plan de surveillance pour votre infrastructure et les applications BizTalk**  
  
-   Lire les rubriques de surveillance dans ce guide pour vous assurer d’une solution d’analyse plus complète. Facteurs à prendre en considération sont les suivants :  
  
    -   Responsables de l’exécution du plan quotidien, hebdomadaire, mensuelle et en tant que tâches d’analyse nécessaires ?  
  
    -   Un utilisateur est informé d’événements, les messages suspendus ou autres défaillances du système ou une application ?  
  
    -   Les exceptions « attendues » filtré ou donné une priorité inférieure ?  
  
    -   Sont que toutes les instances surveillés pour vous assurer qu’ils continuent en cours d’exécution de l’hôte ?  
  
    -   Sont tous les services personnalisés, journaux des événements personnalisés et des bases de données personnalisées analysés ?  
  
    -   Sont les ordinateurs SQL Server et l’agent SQL Server de BizTalk travaux analysés ?  
  
 **Si possible, installez une application de surveillance comme [!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)] afin d’automatiser la surveillance de votre infrastructure et les applications BizTalk Server**  
  
-   À l’aide de Microsoft System Center Operations Manager est la meilleure approche pour automatiser le contrôle, car les packs d’administration de BizTalk Server fournissent des centaines de règles intégrées pour BizTalk Server.  
  
     Pour plus d'informations, consultez les ressources ci-dessous.  
  
    -   [Pack d’administration de Microsoft BizTalk Server pour System Center Operations Manager 2007](http://go.microsoft.com/fwlink/?LinkID=190339) (http://go.microsoft.com/fwlink/?LinkID=190339).  
  
    -   [Comment importer un Pack d’administration dans Operations Manager 2007](http://go.microsoft.com/fwlink/?LinkID=98348) (http://go.microsoft.com/fwlink/?LinkID=98348)  
  
    -   [Comment marquer des bases de données BizTalk Server pour une surveillance personnalisée](../technical-guides/how-to-mark-biztalk-server-databases-for-customized-monitoring.md)  
  
 **Exécuter BizTalk Server Best Practices Analyzer**  
  
-   BizTalk Server Best Practices Analyzer examine un déploiement de BizTalk Server et génère une liste des problèmes liés aux normes de meilleures pratiques. L’outil effectue une vérification au niveau de la configuration en collectant des données à partir des informations différentes sources, telles que les classes Windows Management Instrumentation (WMI), les bases de données SQL Server et les entrées de Registre. Les données sont ensuite utilisées pour évaluer la configuration de déploiement. L’outil lit les rapports uniquement et ne modifie pas les paramètres système et n’est pas un outil de réglage automatique.  
  
     Vous pouvez télécharger BizTalk Server Best Practices Analyzer à [http://go.microsoft.com/fwlink/?LinkId=83317](http://go.microsoft.com/fwlink/?LinkId=83317) (http://go.microsoft.com/fwlink/?LinkId=83317).  
  
 **Exécutez l’outil d’analyse des journaux de performances (PAL)**  
  
-   La publication est disponible en téléchargement gratuit à [https://github.com/clinthuffman/PAL](https://github.com/clinthuffman/PAL). Pour plus d’informations importantes sur l’installation, consultez [à l’aide de l’outil performances analyse des journaux (PAL)](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md).  
  
 **Exécuter l’Analyseur de journal**  
  
-   Log Parser est un outil puissant et flexible qui fournit l’accès de requête universel à des données texte tels que les fichiers journaux, les fichiers XML et fichiers CSV, et sources de données clés sur le système d’exploitation Windows® tels que le journal des événements, le Registre, le système de fichiers et actif Directory®. Voulez-vous utiliser cet outil pour interroger une quantité importante d’informations de journalisation. Vous pouvez télécharger l’outil Analyseur de journal à [http://go.microsoft.com/fwlink/?LinkID=85574](http://go.microsoft.com/fwlink/?LinkID=85574)  
  
 **Exécutez l’outil BizTalk MsgBoxViewer**  
  
 Exécutez le [BizTalk MsgBoxViewer outil](http://go.microsoft.com/fwlink/?LinkId=151930) disponible à partir de [http://go.microsoft.com/fwlink/?LinkId=151930](http://go.microsoft.com/fwlink/?LinkId=151930). Cet outil analyse la BizTalk MessageBox et autres bases de données et génère un rapport HTML contenant des avertissements, si et autres informations relatives aux bases de données. Vous pouvez également enregistrer les rapports pour une utilisation ultérieure. Ces rapports peuvent être utiles lors de la résolution des problèmes avec l’application BizTalk.  
  
 Si l’outil BizTalk MsgBoxViewer identifie les éventuels problèmes, exécutez le [outil de marque de fin](http://go.microsoft.com/fwlink/?LinkId=151931) disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=151931](http://go.microsoft.com/fwlink/?LinkId=151931). Cet outil permet aux utilisateurs de facilement résoudre les problèmes identifiés par l’outil BizTalk MsgBoxViewer. Pour plus d’informations sur la façon dont l’outil de marque de fin s’intègre avec l’outil BizTalk MsgBoxViewer, consultez [à l’aide de BizTalk Terminator pour résoudre les problèmes identifiés par BizTalk MsgBoxViewer](http://go.microsoft.com/fwlink/?LinkId=151932) (http://go.microsoft.com/fwlink/?LinkId=151932).  
  
> [!NOTE]  
>  Utilisation de ces outils n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ces programmes. L'utilisation de ces programmes relève de votre seule responsabilité.  
  
 **Faciliter la surveillance d’une priorité**  
  
-   L’analyse cohérent d’infrastructure et les applications de BizTalk Server est essentielle pour maintenir un environnement sain.  
  
-   Régulièrement, évaluer et ajuster vos outils d’analyse dans le temps et en tant que vos applications BizTalk Server et la modification de l’infrastructure.