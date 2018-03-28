---
title: Vue d’ensemble du processus de développement BAM | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 098db3f6-2a61-4cc8-88c7-2299c2e2a55e
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78ae5f1c61f2a00359e88acd75c093e2b6c2fb91
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="overview-of-the-bam-development-process"></a>Vue d'ensemble du processus de développement BAM
Cette rubrique décrit le processus de développement ainsi que la base de données et les tables où sont stockées les données BAM.  
  
## <a name="prerequisites-for-developing-with-bam"></a>Conditions préalables pour le développement à l'aide des outils BAM  
 Pour commencer à développer à l'aide des outils BAM, vous devez remplir les conditions suivantes :  
  
-   Pour instrumenter une application, vous devez avoir déployé une activité.  
  
-   Vous devez disposer de droits DBO dans les bases de données du serveur SQL et être membre du contexte de sécurité BAM Event Writer Role.  
  
-   Vous devez utiliser Microsoft .NET 4 pour développer votre application. Bien que vous puissiez utiliser n'importe quel langage .NET, il est recommandé d'utiliser C#.  
  
-   Vous devez avoir installé Microsoft.BizTalk.BAM.EventObservation.dll sur votre ordinateur : Vous pouvez obtenir le DLL de deux manières :  
  
    -   Utilisez le gestionnaire de configuration de BizTalk Server pour installer les outils BAM. Nous vous recommandons d'utiliser le gestionnaire de configuration car il inscrit dans le registre des entrées qui simplifient les mises à jour. Pour plus d’informations sur la configuration BAM, consultez [configuration BAM Tools Using the Configuration Manager](http://go.microsoft.com/fwlink/?LinkId=70561) (http://go.microsoft.com/fwlink/?LinkId=70561).  
  
    -   Copiez le DLL à partir d'un ordinateur sur lequel il a déjà été installé. Le DLL se trouve dans Microsoft BizTalk Server \<version\>dossier \Tracking.  
  
## <a name="bam-development-process"></a>Processus de développement BAM  
 L'illustration suivante décrit le flux de développement BAM.  
  
 ![Flux de travail de développement BAM](../core/media/dwb-bamdevelopmentflowc.gif "dwb_bamdevelopmentflowc")  
  
 La procédure suivante décrit les étapes de développement de base d'une solution à l'aide des outils BAM.  
  
#### <a name="to-develop-a-bam-enabled-solution"></a>Pour développer une solution BAM  
  
1.  Créez un modèle d'observation à l'aide du complément BAM pour Excel.  
  
    > [!NOTE]
    >  Exemples des étapes de cette procédure sont accessibles dans l’API BAM (exemple BizTalk Server) à [ http://go.microsoft.com/fwlink/?LinkId=69968 ](http://go.microsoft.com/fwlink/?LinkId=69968).  
  
2.  Utilisez l'utilitaire de gestion de l'analyse BAM pour déployer l'activité dans la PID.  
  
3.  Instrumentez l'application en ajoutant votre code BAM EventStream.  
  
4.  Exécutez l'application. À ce moment-là, le code va :  
  
    -   Ajouter un enregistrement de l’espace réservé dans la table BAM_\<*nom de l’activité*\>_Active table.  
  
    -   Mettre à jour les éléments de données dans l'enregistrement.  
  
    -   Terminer l’activité et déplacer l’enregistrement dans la table BAM_\<* nom d’activité **\>_terminée.  
  
## <a name="where-bam-data-is-stored"></a>Espace de stockage des données BAM  
 L'analyse BAM fournit l'espace de noms EventObservation qui contient les classes EventStream utilisées dans la gestion des événements BAM.  
  
 Les données de suivi BAM sont stockées dans la base de données d'importation principale BAM (PID). Lorsque vous déployez un modèle d'observation à l'aide de l'utilitaire de gestion de l'analyse BAM, les cinq tables suivantes sont créées dans la PID.  
  
|Nom| Description|  
|----------|-----------------|  
|Table active|Nommée bam_\<*nom de l’activité*\>_Active, cette table contient les activités de ce type qui n’ont pas encore terminée.|  
|Table des relations actives|Nommée bam_\<*nom de l’activité*\>_relationsactives, cette table contient les activités associées à l’activité qui n’ont pas encore terminée.|  
|Table des continuations|Nommée bam_\<*nom de l’activité*\>_continuations, ce tableau répertorie les activités de continuation pour l’activité.|  
|Table terminée|Nommée bam_\<*nom de l’activité*\>_completed.|  
|Table des relations terminées|Nommée bam_\<*nom de l’activité*\>_relationsterminées, cette table contient les activités terminées associées à l’activité.|  
  
 Vous pouvez capturer quatre types de données dans une activité BAM :  
  
-   Chaîne  
  
-   Données/Heure (communément appelées étapes majeures)  
  
-   Entier  
  
-   Float