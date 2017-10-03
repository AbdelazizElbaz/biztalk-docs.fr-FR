---
title: "Tâches de surveillance de routine | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2f9f56a-c839-4108-933d-69b00a1e3817
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d91a49393e2b43c9cf39add35e06c5bd864782e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="routine-monitoring-tasks"></a>Tâches de surveillance de routines
Effectuer les tâches d’analyse selon une planification régulière vous aidera à conserver votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] infrastructure opérationnels et les applications.  
  
## <a name="daily-monitoring-tasks"></a>Analyse des tâches quotidiennes  
  
-   Consultez toutes les alertes actives.  
  
-   Utilisez le **Hub du groupe** page dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration pour examiner l’orchestration, de port et d’échecs de messages. Le **Hub du groupe** page permet d’accéder à l’état actuel en temps réel du système, l’accès aux données dans la base de données MessageBox. Vous pouvez afficher toutes les instances de service telles que les orchestrations, les ports et la messagerie, ainsi que les messages qui leur sont associés. À l’aide de la **Hub du groupe** page, vous pouvez effectuer les activités suivantes :  
  
    -   Consultez les instances de service, tels que les orchestrations en cours d’exécution et de messagerie et de leurs messages associés.  
  
    -   rechercher dans la base de données MessageBox une vue des données actives et de l'état en temps réel du système ;  
  
    -   interrompre, terminer et reprendre les instances de service.  
  
     Pour plus d’informations sur l’utilisation de la **Hub du groupe** des pages, consultez [http://go.microsoft.com/fwlink/?LinkId=155281](http://go.microsoft.com/fwlink/?LinkId=155281).  
  
-   Consultez les avertissements (facultatif).  
  
 Pour plus d’informations, consultez [liste de vérification : réalisation de vérifications de Maintenance quotidienne](../technical-guides/checklist-performing-daily-maintenance-checks.md).  
  
## <a name="weekly-monitoring-tasks"></a>Analyse des tâches hebdomadaires  
  
-   Passez en revue les journaux des événements au moins une fois par semaine. La raison de cette tâche consiste à empêcher les problèmes, tels que des erreurs DBNetLib passe inaperçue. Interruption de service peut passer inaperçue, sauf si vous avez un système très faible latence. Toutefois, certaines de ces erreurs peuvent indiquer un problème de plus grand (par exemple, trop d’ordinateurs hôtes ou serveurs BizTalk Server pour le nombre de boîtes de message, des problèmes de performances dans la zone SQL, etc.).  
  
 Pour plus d’informations, consultez [liste de vérification : réalisation de vérifications de Maintenance hebdomadaire](../technical-guides/checklist-performing-weekly-maintenance-checks.md).  
  
## <a name="as-needed-tasks"></a>En fonction des tâches  
  
-   Modifier les règles pour personnaliser l’analyse de vos [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications et l’infrastructure.  
  
-   Exécutez l’outil d’analyse des journaux de performances (PAL). Si votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement est relativement constant (par exemple, nouveaux partenaires commerciaux ne sont pas ajoutés régulièrement, nouveau code n'est pas déployé), vous pouvez exécuter Perfmon et PAL une fois par trimestre ou même tous les six mois. Si votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les modifications de déploiement plus fréquemment, vous souhaiterez Exécutez Perfmon et PAL quelques mois à comparer à une ligne de base. Pour plus d’informations sur la publication, consultez [à l’aide de l’outil performances analyse des journaux (PAL)](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md).  
  
-   Exécution de Perfmon mois, et une fois par trimestre ou même de six mois en fonction du nombre de modifications se produisent dans votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement.  
  
-   Exécuter BizTalk Server Best Practices Analyzer lorsque la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les modifications de déploiement (par exemple, l’ajout de nouvelles applications) ou de la création de nouveaux ordinateurs hôtes. Vous pouvez télécharger BizTalk Server Best Practices Analyzer à [http://go.microsoft.com/fwlink/?LinkId=83317](http://go.microsoft.com/fwlink/?LinkId=83317).  
  
-   Exécutez le [BizTalk MsgBoxViewer outil](http://go.microsoft.com/fwlink/?LinkId=151930) (http://go.microsoft.com/fwlink/?LinkId=151930). Cet outil analyse la BizTalk MessageBox et autres bases de données et génère un rapport HTML contenant des avertissements, si et autres informations relatives aux bases de données.  
  
    > [!TIP]  
    >  Vous pouvez également enregistrer les rapports pour une utilisation ultérieure. Ces rapports peuvent être utiles lors de la résolution des problèmes avec l’application BizTalk.  
  
    > [!NOTE]  
    >  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
-   Exécutez le [outil de marque de fin](http://go.microsoft.com/fwlink/?LinkId=151931) (http://go.microsoft.com/fwlink/?LinkId=151931). Cet outil permet aux utilisateurs de facilement résoudre les problèmes identifiés par l’outil BizTalk MsgBoxViewer. Pour plus d’informations sur la façon dont l’outil de marque de fin s’intègre avec l’outil BizTalk MsgBoxViewer, consultez [à l’aide de BizTalk Terminator pour résoudre les problèmes identifiés par BizTalk MsgBoxViewer](http://go.microsoft.com/fwlink/?LinkId=151932)(http://go.microsoft.com/fwlink/?LinkId=151932).  
  
    > [!NOTE]  
    >  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="annual-monitoring-tasks"></a>Tâches de surveillance annuels  
  
-   Passez en revue l’efficacité de la surveillance de vos [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications et l’infrastructure.  
  
-   Créer un plan pour apporter les modifications nécessaires dans l’analyse.  
  
## <a name="see-also"></a>Voir aussi  
 [Maintenance de routine des listes de contrôle](../technical-guides/routine-maintenance-checklists.md)