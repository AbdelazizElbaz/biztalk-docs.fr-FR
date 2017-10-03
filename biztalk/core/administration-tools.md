---
title: "Outils d’administration et de performances | Documents Microsoft"
description: "Outils courants pour gérer les tâches, les performances et le suivi dans BizTalk Server"
ms.custom: 
ms.date: 09/04/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.ops.admintools
ms.assetid: 932814f7-2ab3-45cb-8bbc-eaf00fcb24a0
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc7420fa6bd59e3653f510e96d41015d266bcebc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="administrative-and-performance-tools"></a>Outils d’administration et de performances 

## <a name="tools-list"></a>Liste des outils
Vous pouvez utiliser les outils suivants pour administrer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], gérer les groupes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], déployer les applications [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], interagir avec les partenaires commerciaux et surveiller l'état de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   **Console d’Administration de BizTalk Server**. la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est l'outil de gestion principal de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cette console fournit une interface utilisateur graphique pour exécuter toutes les opérations de déploiement d'une application BizTalk. Par exemple, elle permet de lancer les Assistants Importation, Installation et Exportation, mais aussi d'ajouter des artefacts à une application et d'en supprimer, et d'apporter d'autres modifications à l'application.  
  
     La console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'afficher les données d'événement de message ou d'instance de service actives ou archivées pour suivre le fonctionnement de votre implémentation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], identifier les goulots d'étranglement et surveiller l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez afficher les détails techniques d'une orchestration, d'un pipeline ou d'une instance de message spécifique, et afficher le flux d'un message particulier qui entre dans le système.  
  
     Pour plus d’informations sur l’utilisation de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, consultez [à l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md).  
  
-   **Outil de ligne de commande BTSTask**. BTSTask permet d'effectuer de nombreuses tâches administratives depuis la ligne de commande. Pour plus d’informations sur l’utilisation de BTSTask, consultez [référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md).  
  
-   **Écriture de scripts et de programmabilité API**. Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
     Le modèle objet WMI expose et simplifie les interfaces API d'administration. Toutes les API présentent certaines formes des opérations suivantes sur tous les objets qu’ils gèrent : créer, énumérer, modifier et supprimer. WMI présente cette fonctionnalité en maintenant une certaine cohérence pour tous les objets WMI.  
  
-   **Business Activity Monitoring (BAM).** L’analyse BAM utilise Microsoft [!INCLUDE[btsOfficeNoVersion](../includes/btsofficenoversion-md.md)] [!INCLUDE[btsExcel](../includes/btsexcel-md.md)] classeur pour fournir aux utilisateurs un moyen d’afficher une vue holistique en temps réel des processus d’entreprise. Pour plus d’informations sur BAM, consultez [à l’aide de l’analyse BAM](../core/using-business-activity-monitoring.md).  


-   [**BizTalk Health Monitor**](http://blogs.msdn.com/b/biztalkhealthmonitor/ "BizTalk Health Monitor ") a été créé par l’équipe de support BizTalk pour collecter des informations sur un environnement BizTalk, y compris l’utilisation des tables et les problèmes connus. Un rapport est généré avec les problèmes potentiels mis en surbrillance. Envisagez l’exécution de cet outil et la vérification de la sortie sur une base régulière pour aider à maintenir votre environnement BizTalk. Cette opération remplace BizTalk MsbBox Viewer.

-   [**Outil de terminaison BizTalk**](https://www.microsoft.com/download/en/details.aspx?id=2846 "BizTalk terminateur outil") a été créé par l’équipe de support BizTalk pour résoudre les problèmes courants de l’intégrité de base de données se trouvés généralement dans la sortie de la visionneuse de MsgBox BizTalk. Tâches communes incluent la suppression des instances et la purge des tables volumineuses. Pour plus d’informations sur l’outil BizTalk Terminator, accédez à [ce billet](http://blogs.msdn.com/b/biztalkcpr/archive/2011/02/10/using-biztalk-terminator-to-resolve-issues-identified-by-biztalk-msgboxviewer.aspx) dans un Blog des ingénieurs de BizTalk.

-   [**Microsoft BizTalk LoadGen 2007**](https://www.microsoft.com/downloads/details.aspx?FamilyID=c8af583f-7044-48db-b7b9-969072df1689&displaylang=en "Microsoft BizTalk LoadGen 2007") génère des charges de transmission de message pour exécuter des tests de stress pour vos applications Microsoft BizTalk Server et de performances et Fournit des compteurs de performance pour analyser les performances de l’infrastructure BizTalk Server en cours d’exécution.

-   [**BizTalk Server Best Practices Analyzer**](https://www.microsoft.com/downloads/details.aspx?FamilyID=93d432fe-1370-4b6d-aaa8-a0c43c30f5ab "BizTalk Server Best Practices Analyzer") effectue une vérification au niveau de la configuration en lecture et en signalant uniquement. Best Practices Analyzer collecte les données des informations de différentes sources, telles que les classes Windows Management Instrumentation (WMI), les bases de données SQL Server et les entrées de Registre. Best Practices Analyzer utilise les données pour évaluer la configuration de déploiement. Best Practices Analyzer ne modifie pas les paramètres système et n’est pas un outil de réglage automatique.

-   [**Performances analyse des journaux (PAL)**](http://www.codeplex.com/PAL "performances analyse des journaux (PAL)") est un outil puissant qui lit un journal de compteur de performances analyse (n’importe quel format connu) et l’analyse à l’aide de complexe, mais il est connu seuils (fournis). L’outil génère un rapport HTML en fonction graphiquement graphiques des compteurs de performances importants et génère des alertes lorsque les seuils sont dépassés.

-   [**DebugView pour Windows**](https://technet.microsoft.com/en-us/sysinternals/bb896647.aspx "DebugView pour Windows") est une application qui vous permet d’analyser la sortie de débogage sur votre système local ou n’importe quel ordinateur sur le réseau accessible via TCP/IP. Il est capable d’afficher en mode noyau et débogage Win32 de sortie, vous n’avez pas besoin d’un débogueur pour intercepter la sortie de débogage génèrent de vos applications ou les pilotes de périphérique, ni vous devez modifier vos applications ou pilotes pour utiliser la sortie de débogage non standard API.

-   [**Ouvrir une session Parser 2.2**](https://www.microsoft.com/downloads/details.aspx?familyid=890CD06B-ABF8-4C25-91B2-F8D975CF8C07&displaylang=en "journal Parser 2.2") est un outil puissant et flexible qui fournit l’accès de requête universel à des données texte tels que les fichiers journaux, les fichiers XML et fichiers CSV, et sources de données clés sur les fenêtres système d’exploitation tels que le journal des événements, le Registre, le système de fichiers et Active Directory.

-   [**Process Explorer**](https://technet.microsoft.com/en-us/sysinternals/bb896653.aspx "Process Explorer") est utile pour assurer le suivi des problèmes de version de la DLL ou les fuites du handle et donnent une idée de la façon dont Windows et les applications fonctionnent.

-   [**Trace TCP**](http://www.pocketsoap.com/tcptrace/ "TCP Trace") est utilisé pour analyser le trafic de réseau en fonction de texte entre client et serveur. Utile lors de l’utilisation des adaptateurs tels que SOAP, HTTP, POP3 etc. pour afficher le message qui transitent via le réseau.

-   [**DTCPing**](https://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=5e325025-4dcd-4658-a549-1d549ac17644 "DTCPing") est conçue pour aider à résoudre les problèmes de pare-feu Microsoft DTC, comme vous le verrez souvent dans un déploiement multiserveur de BizTalk.

  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’applications et les outils de gestion](../core/application-deployment-and-management-tools.md)