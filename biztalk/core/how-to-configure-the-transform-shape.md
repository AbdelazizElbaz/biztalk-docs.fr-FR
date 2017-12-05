---
title: Comment configurer la forme Transformer | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Orchestration Designer], Transform shape
- Transform shape [Orchestration Designer]
ms.assetid: ca81d153-77a6-4bcc-b14f-8f48469fffe0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8da12d090ae0c14f30defc1d65850c609b964704
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-the-transform-shape"></a>Configuration de la forme Transformer
![](../core/media/ebiz-orch-transform.gif "ebiz_orch_transform")  
Forme Transformer  
  
 Les transformations sont utilisées uniquement lorsque vous construisez des messages, par conséquent, votre **transformer** forme apparaît toujours dans un **construire un Message** forme. Vous pouvez supprimer la **construire un Message** mettre en forme sur l’aire de conception et de supprimer puis le **transformer** forme à l’intérieur, ou vous pouvez simplement supprimer la **transformer** forme sur la conception surface et est le Concepteur d’Orchestration créer englobants **construire un Message** forme pour vous.  
  
> [!NOTE]
>  Tout message source ou de destination dans un **transformer** doit être basée sur un schéma.  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-configure-a-transform-shape"></a>Pour configurer une forme Transformer  
  
1.  Dans la fenêtre Propriétés, cliquez sur le **points de suspension** (**...** ) bouton pour le **Messages d’entrée**, **Messages de sortie**, ou **nom de mappage** propriété.  
  
2.  Utilisez le **transformer la Configuration** boîte de dialogue pour configurer le **transformer** forme.  
  
> [!NOTE]
>  A **transformer** forme peut exister que dans un **construire un Message** forme. Si vous faites glisser un **assignation du Message** partout ailleurs sur l’aire de conception, mettre en forme un nouveau **construire un Message** forme sera créé.  
  
### <a name="important-performance-considerations"></a>Observations importantes concernant les performances  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] optimise la possibilité d'effectuer des transformations sur des messages volumineux en transmettant en continu le document dans la mémoire tout en appliquant la transformation plutôt que de charger l'ensemble du document dans la mémoire en une seule fois. Cette optimisation permet le mappage/la transformation de documents bien plus volumineux que ce que les versions précédentes de BizTalk Server permettaient. Cette optimisation présente des limites lorsqu'une orchestration accepte plusieurs entrées et/ou sorties sur les formes Transformer.  
  
 Si une orchestration accepte plusieurs entrées et/ou sorties sur les formes Transformer, le flux du document n'est pas effectué et l'utilisation de la mémoire augmente considérablement. L'une des solutions possibles consiste à appliquer la ou les transformations dans un pipeline de réception de sorte que l'orchestration n'accepte jamais plus d'une entrée ou une sortie sur une forme Transformer.  
  
### <a name="newexisting-map-file"></a>Fichier de mappage nouveau ou existant  
 Dans cette section, vous pouvez cliquer sur une le **nouveau mappage** ou **mappage existant** case d’option pour sélectionner un mappage à affecter à la **transformer** forme.  
  
 Utilisez le **nom** champ sous la case d’option sélectionnée pour spécifier un mappage. Si vous avez sélectionné **nouveau mappage**, vous pouvez entrer une description de la carte que vous souhaitez affecter. Lorsque vous utilisez la **nouveau mappage** option, vous devez spécifier le nom qualifié complet de la carte dans la zone de texte. La zone de texte affiche un exemple de nom par défaut, car il est préremplie avec un nom d’identificateur unique en fonction de l’espace de noms du projet et **transformer** nom de la forme : \<espace de noms de projet\>.\< Nom de la forme de transformation\>_Map (par exemple, MonProjet.transformer3_map).  
  
 Si vous avez sélectionné **mappage existant**, cliquez sur la flèche vers le bas dans la **nom** champ pour sélectionner le fichier de mappage à utiliser. Cette liste, classée par ordre alphabétique, contient tous les mappages existants disponibles pour le projet. Dans cette liste, si vous cliquez sur le texte \<sélectionner dans l’assembly référencé\>, le **sélectionner le Type d’artefact** boîte de dialogue s’affiche. Pour plus d’informations sur les sélections disponible, consultez [l’utilisation de la boîte de dialogue du Type d’artefact de sélectionner](../core/how-to-use-the-select-artifact-type-dialog-box.md).  
  
### <a name="select-source-and-destination-messages"></a>Sélection des messages sources et des messages de destination  
 Cette partie de la **transformer la Configuration** boîte de dialogue pour configurer le mappage que vous avez sélectionné dans le **du fichier de mappage nouveau ou existant ?** section. Si vous avez sélectionné **nouveau mappage** dans cette section, vous créez ce mappage en le configurant dans cette section.  
  
 Si vous avez sélectionné **mappage existant**, vous pouvez utiliser cette section pour effectuer l’une des deux éléments suivants :  
  
-   Sélectionnez un mappage existant à réutiliser tel quel dans la transformation active.  
  
-   Sélectionnez un mappage existant à modifier (reconfigurer), puis utilisez-le avec sa nouvelle configuration dans la transformation active.  
  
 Spécifiez les messages source et de destination à l’aide de la **Messages sources** et **Messages de Destination** contrôles de grille. Ces contrôles de grille permettent de modifier le fichier de mappage de diverses manières. Si vous supprimez un message (une ligne dans un contrôle de grille), ajoutez un message ou sélectionnez un message de type différent, vous modifiez la structure du mappage. Lorsque vous modifiez la structure d'un mappage, vous devez modifier toutes les autres transformations qui l'utilisent pour qu'elles correspondent à la nouvelle structure du mappage. D'autres modifications, comme la suppression d'un message et l'insertion à sa place d'un message de même type, ne modifient pas la structure du mappage.  
  
 Le **Messages sources** et **Messages Destination** contrôles de grille sont identiques dans l’apparence et le comportement. Chaque contrôle de grille comporte deux colonnes : Message et le Type. Vous complétez les contrôles de grille en sélectionnant des messages dans la colonne Message. (Vous ne remplissez que la colonne Message, car la colonne Type est en lecture seule.) Les cellules de la colonne Message possèdent des listes déroulantes complétées par les instances de messages qui se trouvent dans l'étendue de l'orchestration active.  
  
 Vous pouvez sélectionner une ligne dans le contrôle de grille en cliquant sur le *flèche droite* (>) situé à gauche du contrôle de grille. Une fois la ligne sélectionnée, appuyez sur la touche Suppr pour la supprimer. La suppression d'une ligne (message) modifie la structure du fichier de mappage qui la contient. Seuls les fichiers de mappage locaux du projet peuvent être modifiés.  
  
### <a name="when-i-click-ok-launch-the-biztalk-mapper"></a>Lancer le Mappeur BizTalk, après avoir cliqué sur OK  
 En cliquant sur **après avoir cliqué sur OK, lancer le Mappeur BizTalk** Mappeur BizTalk s’ouvre automatiquement lorsque vous cliquez sur **OK** pour fermer la **transformer la Configuration** boîte de dialogue zone et enregistrer vos modifications. En revanche, vous ne pouvez pas enregistrer les modifications s'il manque des informations obligatoires. Dans ce cas, complétez les champs dans la boîte de dialogue, puis **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos des mappages](../core/about-maps.md)   
 [Construction de Messages](../core/constructing-messages.md)   
 [Comment utiliser des Expressions pour transformer dynamiquement des Messages](../core/how-to-use-expressions-to-dynamic-transform-messages.md)