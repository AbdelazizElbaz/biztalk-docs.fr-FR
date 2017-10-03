---
title: Business Activity Monitoring (BAM) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, tools
- utilities, Tracking Profile Deployment Utility
- BAM, deployment process
- BAM
- BAM, presentation layers
- BAM, Tracking Profile Deployment utility
- BAM, about BAM
- BAM, data storage
- BAM Management utility
- Tracking Profile Deployment utility
- BAM, runtime process
- BAM, design time
- BAM, data insertion
- BAM, data consumption
- BAM, BAM Management utility
- BAM, processing
ms.assetid: a8ad48b1-6891-4bbb-b125-27d224e49293
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fea5ce33dddc0f40eaabd6ef34e6035e50c9fab9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-activity-monitoring-bam"></a>BAM (Business Activity Monitoring)
Le diagramme suivant illustre l'architecture du composant d'analyse BAM.  
  
 ![](../core/media/architecture-bam-01.gif "architecture_bam_01")  
  
## <a name="tools"></a>Outils  
 Vous pouvez utiliser les outils suivants pour concevoir, développer et déployer des solutions BizTalk qui s'intègrent au composant BAM.  
  
-   **Microsoft Excel**. Le complément BAM pour Excel fournit une interface utilisateur qui guide les analystes d'entreprise pendant la création d'activités et de vues. Excel sert à la fois d'outil de conception pour les analystes d'entreprise et d'outil de consommation de données pour les utilisateurs des activités. Pour plus d’informations sur le complément BAM pour Excel, consultez [conditions requises pour utiliser le complément BAM pour Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md).  
  
-   **Utilitaire de gestion BAM**. Cet outil permet de déployer dans l'entreprise les définitions BAM créées dans Excel. Il crée les bases de données SQL Server, les cubes Analysis Services, les bases de données des services de notification SQL et les tâches DTS ou SSIS (suivant la version de SQL Server qui est installée) nécessaires. Pour plus d’informations sur le gestionnaire BAM, consultez [l’utilitaire de gestion BAM](../core/bam-management-utility.md).  
  
-   **Éditeur de modèle de suivi**. Cet éditeur permet aux développeurs BizTalk de mapper les éléments de données définis par les analystes d'entreprises dans l'implémentation BizTalk, y compris dans les orchestrations et la messagerie. Pour plus d’informations sur l’éditeur de modèle de suivi, consultez [éditeur](../core/tracking-profile-editor.md).  
  
-   **Utilitaire de déploiement de profil de suivi**. Cet utilitaire permet aux informaticiens de déployer des modèles de suivi dans l'infrastructure BAM, nouveaux ou mis à jour. Pour plus d’informations sur l’outil de déploiement de modèle de suivi, consultez [utilitaire](../core/tracking-profile-deployment-utility.md).  
  
## <a name="presentation"></a>Présentation  
 La couche présentation se compose de ce qui suit :  
  
-   **Portail BAM**. Le portail BAM de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] offre une visibilité totale en temps réel d'un processus d'entreprise. Il s’agit d’une fonctionnalité basée sur le Web qui se compose d’une collection de pages ASP.NET. Vous pouvez le personnaliser pour améliorer les performances pour vos utilisateurs. Pour plus d’informations sur le portail BAM, consultez [portail BAM](../core/bam-portal.md).  
  
-   **Microsoft Excel**. Le complément BAM pour Excel fournit une interface utilisateur qui guide les analystes d'entreprise pendant la création d'activités et de vues. Excel sert à la fois d'outil de conception pour les analystes d'entreprise et d'outil de consommation de données pour les utilisateurs des activités. Pour plus d’informations sur le complément BAM pour Excel, consultez [conditions requises pour utiliser le complément BAM pour Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md).  
  
-   **Interface utilisateur personnalisée**. Les ISV et les développeurs peuvent créer des applications personnalisées affichant des données BAM.  
  
## <a name="processing"></a>Traitement  
 La couche traitement se compose de ce qui suit :  
  
-   **Service Web de gestion BAM**. Ce service Web est utilisé par l’application de portail BAM pour communiquer avec les Tables d’importation principale BAM (PIT). La communication avec la base de données s'effectue à l'aide des informations d'identification stockées dans le registre et créées pendant la configuration. Les méthodes exposées par ce service Web utilisable par les clients personnalisés pour obtenir des vues et leurs détails, les activités associées et mises en page de tableau pour n’importe quel utilisateur de tableau croisé dynamique. Elles peuvent aussi servir à gérer les alertes dans la base de données.  
  
-   **Bus d’événements** . Le service Bus d'événements BAM traite les données de suivi (flux) stockées dans une base de données source et les conserve dans un format de table de requêtes dans la base de données de destination.  
  
-   **Services de Notification SQL**. Ces services évaluent les alertes BAM de type Instance et Agréger définies par l'utilisateur.  
  
 Le diagramme suivant présente les processus physiques sous-jacents de l'architecture BAM.  
  
 ![](../core/media/architecture-bam-02.gif "architecture_bam_02")  
  
## <a name="design-time-experience"></a>Expérience au moment du design  
 Le diagramme suivant illustre la phase de conception.  
  
 ![](../core/media/architecture-bam-03.gif "architecture_bam_03")  
  
 Les étapes suivantes décrivent la séquence présentée dans l'illustration ci-dessus.  
  
1.  L'Éditeur de modèle de suivi part du principe que le serveur BizTalk Server est configuré, qu'une définition BAM au moins a été déployée (avec BM.exe) et que l'infrastructure (base de données d'importation principale comprise) a été créée. Il utilise une clé de registre définie pendant la configuration de BizTalk pour déterminer l'emplacement de la base de données de gestion.  
  
    1.  L'analyse BAM énumère les activités contenues dans la base de données d'importation principale, lorsque celle-ci a été détectée. Les développeurs BizTalk sélectionnent les activités déployées qui sont extraites de la base de données d'importation principale BAM.  
  
    2.  Le développeur BizTalk effectue un mappage sur une implémentation physique en parcourant les assemblys déployés extraits de la base de données de gestion BizTalk.  
  
    3.  Au terme du mappage visuel sur les artefacts BizTalk, les métadonnées sont soumises au composant d'exécution de BizTalk Server pour collecter et stocker les données. Cela est réalisé via des annotations (pour les informations relatives aux messages utilisées pour décoder les données collectées) et le modèle de suivi (qui sert à récupérer les données d'exécution).  
  
2.  Microsoft Excel sert à la fois d'outil de conception et d'outil de consommation ou de présentation des données. Il permet aux utilisateurs de construire une définition BAM en créant des activités et des vues BAM, et aussi de créer les contrôles et les graphiques des tableaux croisés dynamiques affichés sur le portail BAM.  
  
## <a name="deployment"></a>Déploiement  
 Il existe deux catégories de déploiement  
  
-   création de l'infrastructure dynamique,  
  
-   instrumentation de l'exécution pour collecter des données.  
  
 Le diagramme suivant illustre le déploiement BAM.  
  
 ![](../core/media/architecture-bam-04.gif "architecture_bam_04")  
  
 Les étapes suivantes décrivent la séquence présentée dans l'illustration ci-dessus.  
  
1.  L'utilitaire de gestion BAM sert à créer l'infrastructure dynamique. Il se sert de la définition BAM ou d'un classeur Excel de conception mais aussi du fichier XML de configuration BAM pour créer toutes les bases de données nécessaires et les tâches DTS ou SSIS correspondantes dont le système a besoin pour fonctionner.  
  
    1.  La base de données d'importation principale BAM et l'ensemble des procédures stockées, déclencheurs et tâches DTS ou SSIS nécessaires sont construits.  
  
    2.  La base de données des archives BAM est définie mais elle n'est pas créée tant que la tâche d'archivage DTS ou SSIS n'est pas exécutée.  
  
    3.  La base de données de schémas en étoile BAM est définie si des agrégations OLAP BAM ont été définies. Vous pouvez déterminer si les agrégations ont été définies si le **RTA** bouton dans la feuille de calcul Excel est désactivé ou **CreateOlapCube** a la valeur **true** dans la définition BAM et le fichier de Configuration XML a une unité de déploiement pour **AnalysisDatabase**.  
  
    4.  Une agrégation non RTA doit être définie pour la définition BAM et pour le fichier de configuration XML afin qu'un cube OLAP BAM puisse être créé.  
  
    5.  La vue éclatée du processus du gestionnaire BAM montre que le processus des services de notification (nscontrol.exe) est appelé pour créer les bases de données NS SQL.  
  
2.  L'interface utilisateur de l'Éditeur de modèle de suivi possède une commande de déploiement qui instrumente l'exécution pour suivre et décoder les données des systèmes d'exécution. Dans ce cas, il exécute un push **annotations** dans la base de données d’importation principale BAM (si les données sont extraites du système de messagerie). Un modèle de suivi est inséré dans la base de données de gestion BizTalk utilisée par le composant d'exécution BizTalk pour déterminer quelles données publier sur le système BAM.  
  
3.  L'outil de ligne de commande de déploiement du suivi BizTalk permet de publier des modèles de suivi dans la base de données d'importation principale BAM et dans la base de données de gestion, d'une manière similaire à ce que fait l'Éditeur de modèle de suivi ; cependant, l'outil de ligne de commande n'autorise pas les mappages.  
  
## <a name="data-consumption"></a>Consommation de données  
 La consommation de données est le processus dans lequel un utilisateur consomme les informations collectées par l'infrastructure BAM. Cela suppose, à ce stade, que la définition BAM a été créée (définir quelles données collecter et comment les afficher), déployée (créer dynamiquement l'infrastructure) et mappée sur l'implémentation physique (définir où collecter les données et dans certains cas écrire le code à transmettre au système).  
  
 Le diagramme suivant illustre le processus de consommation de données.  
  
 ![](../core/media/architecture-bam-05.gif "architecture_bam_05")  
  
 Les étapes suivantes décrivent la séquence présentée dans l'illustration ci-dessus.  
  
1.  Le portail BAM est fractionné en deux processus, Internet Explorer et le processus de portail Web BAM hébergé par Internet Information Services.  
  
    1.  Internet Explorer utilise le contexte de sécurité de l'utilisateur des activités qui se connecte au site Web du portail BAM. Le site Web du portail BAM est une application ASPX qui utilise le service Web de gestion BAM pour collecter des informations.  
  
    2.  Le portail BAM appelle le service Web de gestion BAM pour récupérer des informations comme les activités/vues BAM que l'utilisateur des activités peut consulter. Il est essentiel que le service Web de gestion BAM puisse emprunter l'identité de l'utilisateur des activités. Par conséquent, pour un déploiement type, le portail BAM et le service Web sont hébergés sur le même ordinateur.  
  
        > [!NOTE]
        >  Si votre entreprise prend en charge Kerberos et qu'Active Directory est configuré pour prendre en charge la délégation, il est possible que le portail et le service Web soient implantés sur des machines différentes.  
  
    3.  Le service Web appelle des procédures stockées dans la base de données d'importation principale BAM pour procéder à des vérifications de la sécurité, récupérer des métadonnées et récupérer des informations sur les agrégations BAM en temps réel.  
  
        > [!NOTE]
        >  Le portail BAM utilise actuellement un Service Web non documenté appelé le **Service Web de requêtes**. Ce service n'est pas pris en charge et sera vraisemblablement désapprouvé dans la prochaine version.  
  
    4.  Internet Explorer héberge les contrôles OWC (Office Web Controls) qui établissent des connexions directes avec les cubes BAM Analysis Services.  
  
2.  Excel  
  
## <a name="runtime"></a>Runtime  
 Quand la définition BAM a été créée et l'infrastructure générée, et que le développeur a instrumenté les systèmes nécessaires pour activer la visibilité, les données peuvent commencer à circuler dans le système.  
  
### <a name="data-insertion"></a>Insertion de données  
 Le service BizTalk (BTSNTSvc.exe) est l'un des principaux vecteurs pour la circulation des données dans le système BAM. Il est conçu de façon à pouvoir contenir des sous-systèmes logiques.  
  
 Le diagramme suivant illustre ce processus.  
  
 ![](../core/media/architecture-bam-06.gif "architecture_bam_06")  
  
 Les étapes suivantes décrivent la séquence présentée dans l'illustration ci-dessus.  
  
1.  Un sous-système héberge le moteur BizTalk Server chargé d'exécuter les orchestrations et la messagerie.  
  
2.  Le service Bus d'événements est un autre sous-système, chargé d'écrire les données du flux d'événements mises en mémoire tampon dans la base de données d'importation principale BAM.  
  
### <a name="booting-the-runtime"></a>Démarrage du composant d'exécution  
 Lorsque le service BizTalk est démarré, chaque sous-système charge les métadonnées nécessaires à son fonctionnement.  
  
 Le diagramme suivant illustre ce processus.  
  
 ![](../core/media/architecture-bam-07.gif "architecture_bam_07")  
  
 Les étapes suivantes décrivent la séquence présentée dans l'illustration ci-dessus.  
  
1.  Quand le moteur BizTalk (orchestrations ou messagerie) s'exécute, il appelle des intercepteurs qui régulent le flux des données entre le moteur et BAM. Quand le moteur appelle l'intercepteur, ce dernier analyse où en est le moteur par rapport à l'ordre d'exécution des artefacts d'orchestration ou de messagerie. Si des données doivent être récupérées à l'emplacement où le moteur s'exécute actuellement, l'intercepteur collecte ces données. Les métadonnées déterminant l'emplacement et la nature des données à capturer sont stockées dans le modèle de suivi. Pendant le démarrage du service BizTalk, les intercepteurs du moteur contacteront la base de données de gestion BizTalk pour extraire le modèle de suivi correspondant aux artefacts en cours d'exécution.  
  
2.  Le service Bus d'événements a pour fonction principale de convertir les données de type Blob (écrites par le moteur BizTalk) en éléments de données exploitables et d'insérer les données dans la base de données d'importation principale BAM. L'intercepteur de messagerie écrit les données brutes sous une forme compressée. Cela évite d'avoir une plage de travail mémoire trop étendue. Pour que le service Bus d'événements puisse convertir les données de messagerie en éléments de données exploitables, il doit d'abord charger des métadonnées capables d'interpréter les données brutes. Ces métadonnées sont appelée **annotations**. Elles ont été placées par l'Éditeur de modèle de suivi ou par l'outil de ligne de commande de déploiement de modèle de suivi. Si la solution déployée ne récupère pas de données de la messagerie, il n'y aura pas d'annotations. Les intercepteurs d'orchestration codent suffisamment d'informations brutes pour que le service Bus d'événements puisse décoder correctement sans devoir recourir à des annotations supplémentaires.  
  
### <a name="storing-data"></a>Stockage des données  
 Cette section explique comment les données sont capturées à partir du service BizTalk.  
  
 Le diagramme suivant illustre ce processus.  
  
 ![](../core/media/architecture-bam-08.gif "architecture_bam_08")  
  
 Les étapes suivantes décrivent la séquence présentée dans l'illustration ci-dessus.  
  
1.  Le moteur BizTalk, comme décrit précédemment, est doté d'intercepteurs appelés pendant l'exécution des orchestrations et des solutions de messagerie. À partir des informations du modèle de suivi, les intercepteurs déterminent quelles données capturer puis envoient ces dernières à la base de données MessageBox BizTalk sous forme binaire. Une table TrackingData stocke les données de type Blob sérialisées capturées pendant l'exécution. Pendant le traitement, il arrive que le moteur doive stocker des données qu'il conserve en mémoire pendant l'exécution. Ces données constituent des « points de persistance » et le moteur décide quand ces points sont créés. Quand un point de persistance est créé, les données précédemment capturées à partir des intercepteurs sont vidées et conservées lors d'une même transaction. Cela garantit la cohérence des données dans le moteur et, à terme, ce que l'analyse BAM peut consulter. En cas de défaillance et si la transaction est annulée, les données BAM associées sont annulées aussi.  
  
2.  Le service Bus d'événements est hébergé dans le même processus exécutable que le moteur. Il obtient ses données de la table TrackingData stockée par le moteur BTS (ou de toute autre source de données BufferedEventStream). L’image représente un assembly – Microsoft.BizTalk.Bam.EventObservation. Cet assembly n’expose pas une méthode de récupération des données à partir de la classe BufferedEventStream. Ce code est hébergé dans le service Bus d'événements. Les données sont récupérées puis préparées afin d'être stockées dans la base de données d'importation principale. La plupart des données binaires sont des objets ..NET sérialisés qui sont réalimentés à partir des propriétés transférées de l'objet vers des instructions SQL formatées.  
  
3.  Quand le stockage des données survient, le service Bus d'événements tente de stocker un lot volumineux. Ce lot contient les appels de procédures stockées générés par l'outil de déploiement du gestionnaire de l'analyse BAM. Une forte activité sur la base de données ou d'autres conditions entraînant un verrouillage de table peut entraîner l'échec du stockage du lot. En cas d'échec, deux autres tentatives sont faites. Si elles échouent, le lot est divisé en plus petits lots et le stockage est tenté à nouveau. En cas d'échec, le lot est transféré dans la table FailedTracking.  
  
### <a name="custom-data-insertion"></a>Insertion de données personnalisées  
 La section précédente décrivait en détail la récupération de données par l'analyse BAM sur l'hôte BizTalk Server à l'aide de diverses méthodes : indirectement avec l'Éditeur de modèle de suivi pour créer un modèle, et plus directement avec les méthodes de flux d'événements directement dans le code. Toutefois, toutes les données pertinentes pour l'analyse BAM ne sont pas nécessairement disponibles dans BizTalk. C'est pourquoi un assembly est disponible pour les applications personnalisées.  
  
 Le diagramme suivant illustre ce processus.  
  
 ![](../core/media/architecture-bam-09.gif "architecture_bam_09")  
  
 Les étapes suivantes décrivent la séquence présentée dans l'illustration ci-dessus.  
  
1.  L’application personnalisée doit être en mesure de charger le [Microsoft.BizTalk.Bam.EventObservation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.aspx) assembly pour accéder aux méthodes d’insertion de données dans une activité BAM BAM. Deux classes principales sont exposées, DirectEventStream et BufferedEventStream. Dans l'illustration ci-dessus, la classe DirectEventStream est mise en évidence. Elle écrit directement dans la base de données d'importation principale. Il s'agit de la méthode la plus courante pour écrire des données dans une activité BAM.  
  
2.  À l'instar de la méthode dans laquelle BizTalk stocke des données, la classe BufferedEventStream écrit des données binaires de type Blob dans une base de données indirecte. Dans ce cas, la base de données MessageBox BizTalk sert de magasin intermédiaire. Le choix de la classe dépend de plusieurs facteurs ; toutefois, les performances sont une préoccupation essentielle. La classe BufferedEventStream traite les données par lots et offre un débit plus élevé mais présente l'inconvénient de ne pas écrire les données immédiatement.  
  
3.  Comme la méthode BizTalk d'insertion de données, le service Bus d'événements traitera les données binaires, les décodera et les stockera dans la base de données d'importation principale BAM. Cela n'est nécessaire que pour les données écrites via la classe BufferedEventStream.  
  
## <a name="distributed-navigation"></a>Navigation distribuée  
 Le composant de navigation distribuée du portail BAM permet aux utilisateurs de voir les relations d'activité au-delà des limites distantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion et l’Architecture de suivi](../core/management-and-tracking-architecture.md)