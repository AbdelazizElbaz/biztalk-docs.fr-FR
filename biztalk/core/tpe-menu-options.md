---
title: "Les Options de Menu de l’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, menu options
- activities [BAM], importing
- activities [BAM], definitions
ms.assetid: 5179fcb5-6dab-481d-ad89-3868c8b07383
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b5162d05f9daa591458acaf87aefd86478ef70d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tpe-menu-options"></a>Options de menu de l'Éditeur de modèle de suivi
Cette rubrique décrit les options de menu de l'Éditeur de modèle de suivi. Les menu principal contient les options Fichier, Outils et Aide.  
  
 Des fonctionnalités supplémentaires, propres à l'interception de messages, s'affichent dans les menus contextuels des éléments de la vue Activité, dans le volet gauche de l'application.  
  
## <a name="file-menu"></a>Menu Fichier  
 Le menu Fichier contient les options suivantes :  
  
-   **Nouvelle** – crée un nouveau profil de suivi. Cette option est toujours disponible.  
  
-   **Ouvrez** – ouvre un modèle de suivi. Cette option est toujours disponible.  
  
-   **Enregistrer** – enregistre le profil de suivi en cours de modification. Si aucun modèle de suivi ne se trouve en cours de modification, cette option n'est pas disponible.  
  
-   **Enregistrer en tant que** : enregistre le profil de suivi en cours de modification à un nom que vous spécifiez. Si aucun modèle de suivi ne se trouve en cours de modification, cette option n'est pas disponible.  
  
-   **Importer la définition d’activité BAM** – importe une définition d’activité qui a été appliquée. Cet élément de menu a la même fonction que le lien apparaissant en filigrane dans le frame de gauche, c'est-à-dire que l'utilisateur peut démarrer l'action indifféremment à l'aide de l'une ou l'autre option, le lien en filigrane pouvant ici être assimilé à un conseil d'utilisation. Cette option est toujours disponible lorsqu'une connexion à la base de données de gestion BizTalk et à la base de données d'importation principale BAM est en cours.  
  
-   **Sortie** – quitte l’éditeur. Lorsque vous quittez l'application pendant une modification, une fenêtre Enregistrer ou Enregistrer sous s'affiche, comme dans toute application Windows. Cette option est toujours disponible.  
  
### <a name="new-profile"></a>Nouveau profil  
 Le **nouveau profil** option de menu ouvre un espace suivi de fichier de source de profil avec aucun contenu par rapport à un fichier BTT vide (fichier de modèle de suivi). TrackingProfile1 (2, 3, etc.) est le nom attribué par défaut au nouveau modèle de suivi.  
  
> [!NOTE]
>  Par défaut, la base de données de gestion BizTalk est paramétrée sur celle du groupe BizTalk. Pour modifier la base de données de gestion, utilisez le **Set Mgmt DB** option sur le **outils**. La configuration de la base de données de gestion BizTalk est conservée entre les sessions.  
  
### <a name="open"></a>Ouvrir  
 Le **ouvrir** option de menu permet à l’utilisateur rechercher et sélectionner un seul profil avec lequel travailler. Ces modèles dépendent de la disponibilité des assemblys sur lesquels ils reposent pour pouvoir être affichés et validés.  
  
 Si l’assembly déployé d’origine n’est plus disponible, ou vous devez modifier l’assembly auquel le profil est associé, vous avez la possibilité d’appeler explicitement la **Set Mgmt DB** action pour actualiser le lien. Vous pouvez également modifier le profil et l'appliquer.  
  
### <a name="save"></a>Enregistrer  
 Le **enregistrer** option permet d’enregistrer le modèle de suivi en cours de modification. La première fois à enregistrer est activée sur un modèle de suivi l’option appelle la **Enregistrer sous** boîte de dialogue.  
  
### <a name="save-as"></a>Enregistrer sous  
 Le **Enregistrer sous** option vous permet de spécifier le dossier et le nom pour le modèle de suivi. L'extension par défaut d'un fichier de modèle de suivi est .btt.  
  
### <a name="import-bam-activity-definition"></a>Importer une définition d'activité BAM  
 Le **importer une définition d’activité BAM** option ouvre la boîte de dialogue Importer une définition BAM activité qui est remplie avec une liste de définitions d’activité BAM trouvé dans la base de données d’importation principale BAM.  
  
 Cette fonctionnalité est également appelée en cliquant **cliquez ici pour importer un lien de la définition d’activité BAM** dans la vue activité d’un nouveau modèle de suivi.  
  
 **Récupérer la boîte de vérification de profil existant**  
  
 Cette case à cocher vous permet d'extraire et d'inclure des mappages entre des modèles de suivi existants et la définition d'activité.  La case à cocher est désactivée par défaut.  
  
> [!NOTE]
>  Lorsque les définitions d'activité BAM sont importées avec leurs paramètres de suivi, des mappages existants sont validés en fonction des assemblys, des orchestrations, des schémas et des ports de la base de données de gestion actuellement sélectionnée. Si un mappage ne correspond pas aux informations de la base de données, une icône d'erreur s'affiche à côté de celui-ci. Ces erreurs peuvent se produire lorsqu'un modèle de suivi a été déployé avant que le déploiement d'un assembly ait pu être annulé ou lorsque la base de données d'importation principale BAM est partagée par plusieurs groupes et plusieurs bases de données de gestion BizTalk. Dans le dernier cas, les icônes d'erreur s'affichent si le modèle de suivi a été déployé à partir d'un groupe mais importé à partir d'un autre groupe.  
  
### <a name="exit"></a>Quitter  
 Le **Exit** Option ferme l’éditeur. Si une modification a été apportée au modèle de suivi, vous êtes invité à enregistrer le modèle lorsque l'Éditeur se ferme.  
  
## <a name="tools-menu"></a>Menu Outils  
 Le menu Outils contient les options suivantes :  
  
-   **Appliquer le modèle de suivi** – enregistre le profil dans la base de données d’importation principale BAM.  
  
-   **Supprimer le modèle de suivi** : supprime le suivi des mappages à partir de la base de données d’importation principale BAM du profil.  
  
-   **Définir la base de données de gestion** : définit la base de données de gestion qui fonctionne sur l’éditeur.  
  
-   **Options** – permet de définir les options de l’éditeur.  
  
### <a name="apply-tracking-profile"></a>Appliquer un modèle de suivi  
 Le **appliquer le modèle de suivi** option de menu stocke le modèle de suivi à l’assembly spécifié, ainsi que pour les orchestrations et les ports de mappage. Tous les artefacts référencés dans le modèle de suivi doivent être disponibles dans une base de données de gestion BizTalk spécifiée. Toutes les nouvelles instances des services appropriés utilisent le nouveau modèle de suivi au démarrage.  
  
 Vous pouvez travailler en vous servant de plusieurs assemblys à la fois. Vous ne pouvez pas travailler avec ces assemblys simultanément mais plusieurs d'entre eux sont accessibles dans une seule session de modification relative à une définition d'activité BAM.  En d'autres termes, si vous importez une définition d'activité BAM et que vous sélectionnez ensuite trois assemblys dans lesquels récupérer des éléments suivis, le modèle que l'Éditeur de modèle de suivi crée est appliqué à plusieurs modèles associés aux orchestrations et aux ports utilisés dans le modèle de suivi. Le modèle de suivi contient toujours des informations sur tous les assemblys associés à une définition d'activité BAM donnée.  
  
> [!CAUTION]
>  Dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], un seul modèle de suivi peut être déployé d'après une activité BAM. Par conséquent, si vous déployez un modèle dont l'activité correspondante est mappée à une orchestration et que vous déployez ensuite un autre modèle pour lequel la même activité est mappée à des orchestrations différentes, le premier modèle déployé est remplacé.  
  
### <a name="remove-tracking-profile"></a>Suppression d'un modèle de suivi  
 Le **supprimer le modèle de suivi** option de menu supprime le modèle de suivi pour la définition d’activité chargée et ses orchestrations et ports correspondants. Vous êtes invité à confirmer cette action avant qu'elle ne soit terminée.  
  
### <a name="set-management-database"></a>Définir la base de données de gestion  
 Le **définir la base de données de gestion** option de menu spécifie la base de données de gestion BizTalk le mappage de sources peuvent être choisies et via le BAM sont trouvent les définitions d’activité. Par défaut, le modèle de suivi est défini sur la base de données de gestion BizTalk par défaut spécifiée lors de la configuration.  
  
 Chaînes de connexion SQL peuvent être spécifiés dans un des deux manières :  
  
-   en indiquant simplement le nom du serveur, l'Éditeur de modèle de suivi se connectant alors au port par défaut ;  
  
-   Vous pouvez spécifier un nom de serveur et la paire, le nom du serveur, port numéro de port. L'Éditeur de modèle de suivi se connecte alors à l'ordinateur exécutant le serveur SQL qui utilise le port spécifié.  
  
## <a name="help-menu"></a>Menu aide  
 Le menu Aide contient les options suivantes :  
  
-   **Aide de BizTalk Server** – ouvre le fichier d’aide de BizTalk Server.  
  
-   **Aide de l’Éditeur TPE** – ouvre la section de l’éditeur dans le fichier d’aide de BizTalk Server.  
  
-   **BizTalk Server en ligne** -ouvre une aide en ligne de BizTalk Server.  
  
-   **Éditeur de modèle de suivi** – affiche les informations standard relatives.  
  
## <a name="see-also"></a>Voir aussi  
 [Composants de l’éditeur](../core/components-of-the-tpe.md)   
 [Éditeur de modèle de suivi](../core/tracking-profile-editor.md)