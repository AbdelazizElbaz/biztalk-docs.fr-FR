---
title: "Comment importer et exporter des stratégies et des vocabulaires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, exporting
- Rule Engine Deployment Wizard
- policies, importing
- vocabularies, exporting
- vocabularies, importing
ms.assetid: c427f686-5908-4f72-9e72-46a5497274ac
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17ba7cd8a9fc5d28d1b718e9a47ad6cf2f448ec7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-import-and-export-policies-and-vocabularies"></a>Comment importer et exporter des stratégies et des vocabulaires
L'Assistant Déploiement du moteur de règles permet d'importer ou d'exporter une stratégie ou un vocabulaire.  
  
> [!NOTE]
>  Tous les vocabulaires utilisés par une stratégie ou un vocabulaire doivent d'abord être importés, sinon une erreur sera générée.  
  
### <a name="to-import-or-export-a-policy-or-vocabulary"></a>Pour importer ou exporter une stratégie ou un vocabulaire  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Assistant de déploiement du moteur de règles d’entreprise**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans la page d’accueil, cliquez sur **suivant**.  
  
3.  Sur le **la tâche de déploiement** page, sélectionnez **Exporter stratégie/vocabulaire vers le fichier à partir de la base de données** ou **importer et publier la stratégie/vocabulaire à base de données à partir du fichier**, puis Cliquez sur **suivant**.  
  
4.  Sur le **magasin de stratégies** page, dans la liste déroulante, sélectionnez un ordinateur SQL Server disponible et base de données, puis cliquez sur **suivant**.  
  
5.  Sur le **Exporter stratégie/vocabulaire** page, procédez comme suit, puis cliquez sur **suivant**.  
  
    1.  Sélectionnez **stratégie** ou **vocabulaire** selon ce que vous voulez d’exportation/importation.  
  
    2.  À partir de la **stratégie/le vocabulaire** liste déroulante, sélectionnez la stratégie/le vocabulaire souhaité.  
  
    3.  Cliquez sur **Parcourir** pour sélectionner le fichier de définition.  
  
6.  Passez en revue le serveur, base de données et les informations de stratégie ou de vocabulaire, puis cliquez sur **suivant**.  
  
7.  Une fois l’importation ou l’exportation terminée, cliquez sur **suivant**.  
  
8.  Passez en revue l’état d’achèvement de l’importation ou l’exportation, puis cliquez sur **Terminer**.