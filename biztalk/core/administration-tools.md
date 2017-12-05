---
title: "Outils d’administration et de performances | Documents Microsoft"
description: "Outils courants pour gérer les tâches, les performances et le suivi dans BizTalk Server"
ms.custom: 
ms.date: 11/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 932814f7-2ab3-45cb-8bbc-eaf00fcb24a0
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 100b72949cd5fc6ab4da2dd90469f924db27963d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="administrative-and-performance-tools"></a>Outils d’administration et de performances 

## <a name="tools-list"></a>Liste des outils
Vous pouvez utiliser les outils suivants pour administrer BizTalk Server de ServerBizTalk, pour gérer des groupes BizTalk Server, pour déployer des applications BizTalk Server, pour interagir avec des partenaires commerciaux et pour surveiller l’état de BizTalk Server :  
  
-   **Console d’Administration de BizTalk Server**. La console Administration de BizTalk Server est le principal outil de gestion de BizTalk Server. Cette console fournit une interface utilisateur graphique pour exécuter toutes les opérations de déploiement d'une application BizTalk. Par exemple, elle permet de lancer les Assistants Importation, Installation et Exportation, mais aussi d'ajouter des artefacts à une application et d'en supprimer, et d'apporter d'autres modifications à l'application.  
  
     À l’aide de la console Administration de BizTalk Server, vous pouvez utiliser message actives ou archivées affichage événement ou le service de données d’instance pour effectuer le suivi de l’intégrité de votre implémentation de BizTalk Server, identifier les goulots d’étranglement et surveiller l’environnement BizTalk Server. Vous pouvez afficher les détails techniques d'une orchestration, d'un pipeline ou d'une instance de message spécifique, et afficher le flux d'un message particulier qui entre dans le système.  
  
     Pour plus d’informations sur l’utilisation de la console Administration de BizTalk Server, consultez [à l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md).  
  
-   **Outil de ligne de commande BTSTask**. BTSTask permet d'effectuer de nombreuses tâches administratives depuis la ligne de commande. Pour plus d’informations sur l’utilisation de BTSTask, consultez [référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md).  
  
-   **Écriture de scripts et de programmabilité API**. Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
     Le modèle objet WMI expose et simplifie les interfaces API d'administration. Toutes les API présentent certaines formes des opérations suivantes sur tous les objets qu’ils gèrent : créer, énumérer, modifier et supprimer. WMI présente cette fonctionnalité en maintenant une certaine cohérence pour tous les objets WMI.  
  
-   **Business Activity Monitoring (BAM).** BAM utilise un classeur Microsoft Office Excel pour fournir aux utilisateurs un moyen d’afficher une vue holistique en temps réel des processus d’entreprise. Pour plus d’informations sur BAM, consultez [à l’aide de l’analyse BAM](../core/using-business-activity-monitoring.md).  


-   [**BizTalk Health Monitor**](http://blogs.msdn.com/b/biztalkhealthmonitor/ "BizTalk Health Monitor ") a été créé par l’équipe de support BizTalk pour collecter des informations sur un environnement BizTalk, y compris l’utilisation des tables et les problèmes connus. Un rapport est généré avec les problèmes potentiels mis en surbrillance. Envisagez l’exécution de cet outil et la vérification de la sortie sur une base régulière pour aider à maintenir votre environnement BizTalk. Cette opération remplace BizTalk MsbBox Viewer.

-   [**Outil de terminaison BizTalk**](https://www.microsoft.com/download/en/details.aspx?id=2846 "BizTalk terminateur outil") a été créé par l’équipe de support BizTalk pour résoudre les problèmes courants de l’intégrité de base de données se trouvés généralement dans la sortie de la visionneuse de MsgBox BizTalk. Tâches communes incluent la suppression des instances et la purge des tables volumineuses. Pour plus d’informations sur l’outil BizTalk Terminator, accédez à [ce billet](http://blogs.msdn.com/b/biztalkcpr/archive/2011/02/10/using-biztalk-terminator-to-resolve-issues-identified-by-biztalk-msgboxviewer.aspx) dans un Blog des ingénieurs de BizTalk.

-   [**Microsoft BizTalk LoadGen 2007** ](https://www.microsoft.com/download/details.aspx?id=14925) génère des charges de transmission de message pour exécuter des tests de stress pour vos applications de Microsoft BizTalk Server et de performances et fournit des compteurs de performances pour analyser les performances de la infrastructure BizTalk Server en cours d’exécution.

-   [**BizTalk Server Best Practices Analyzer**](https://www.microsoft.com/downloads/details.aspx?FamilyID=93d432fe-1370-4b6d-aaa8-a0c43c30f5ab "BizTalk Server Best Practices Analyzer") effectue une vérification au niveau de la configuration en lecture et en signalant uniquement. Best Practices Analyzer collecte les données des informations de différentes sources, telles que les classes Windows Management Instrumentation (WMI), les bases de données SQL Server et les entrées de Registre. Best Practices Analyzer utilise les données pour évaluer la configuration de déploiement. Best Practices Analyzer ne modifie pas les paramètres système et n’est pas un outil de réglage automatique.

-   [**Performances analyse des journaux (PAL)** ](https://github.com/clinthuffman/PAL) est un outil puissant qui lit un journal de compteur de performances analyse (n’importe quel format connu) et l’analyse à l’aide de seuils complexes, mais il est connus (fournis). L’outil génère un rapport HTML en fonction graphiquement graphiques des compteurs de performances importants et génère des alertes lorsque les seuils sont dépassés.

-   [**DebugView pour Windows** ](https://docs.microsoft.com/sysinternals/downloads/debugview) est une application qui vous permet d’analyser la sortie de débogage sur votre système local ou n’importe quel ordinateur sur le réseau accessible via TCP/IP. Il est capable d’afficher en mode noyau et débogage Win32 de sortie, vous n’avez pas besoin d’un débogueur pour intercepter la sortie de débogage génèrent de vos applications ou les pilotes de périphérique, ni vous devez modifier vos applications ou pilotes pour utiliser la sortie de débogage non standard API.

-   [**Ouvrir une session Parser 2.2** ](https://www.microsoft.com/download/details.aspx?id=24659) est un outil puissant et flexible qui fournit l’accès de requête universel aux données tels que les fichiers journaux, les fichiers XML et fichiers CSV, et les sources de données de clé sur le système d’exploitation Windows tels que le journal des événements du Registre, le système de fichiers et Active Directory.

-   [**Process Explorer** ](https://docs.microsoft.com/sysinternals/downloads/process-explorer) est utile pour assurer le suivi des problèmes de version de la DLL ou les fuites du handle et donnent une idée de la façon dont Windows et les applications fonctionnent.

-   [**Trace TCP**](http://www.pocketsoap.com/tcptrace/ "TCP Trace") est utilisé pour analyser le trafic de réseau en fonction de texte entre client et serveur. Utile lors de l’utilisation des adaptateurs tels que SOAP, HTTP, POP3 etc. pour afficher le message qui transitent via le réseau.

-   [**DTCPing** ](https://www.microsoft.com/download/details.aspx?id=2868) est conçue pour aider à résoudre les problèmes de pare-feu Microsoft DTC, comme vous le verrez souvent dans un déploiement multiserveur de BizTalk.

  
## <a name="see-also"></a>Voir aussi  
 [Outils de gestion et de déploiement d’applications](../core/application-deployment-and-management-tools.md)