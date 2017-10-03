---
title: "Création d’un Port d’envoi A4SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, send ports
- send ports, creating
ms.assetid: d1ee18f8-a6aa-4cd5-9e65-fb2e0fa2d0c2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cf24cb99643acc869123450ce14fd5050ee7408
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-an-a4swift-send-port"></a>Création d’un Port d’envoi A4SWIFT
Vous devez créer un port d’envoi pour activer [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pour envoyer un message au réseau rapide, comme indiqué dans l’illustration suivante. Ce port d’envoi envoie les messages de fichier plat vers un dossier sortant. Ce port d’envoi est conçu pour fonctionner avec la fonctionnalité de Message Repair et New Submission.  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-send-port-configuration.gif "A4SWIFT_Send_Port_Configuration")  
  
 **Résumé**  
  
 Créer et démarrer un port d’envoi unidirectionnel statique avec les propriétés et les composants suivants :  
  
|Propriété/composant|Paramètre|  
|-------------------------|-------------|  
|Port d'envoi|Port statique unidirectionnel|  
|Type de transport |FILE|  
|Dossier de destination (adresse URI)|Nom du dossier que vous souhaitez envoyer des messages à partir de|  
|Nom de fichier (adresse URI)|%MessageID%.txt|  
|Filtres|Comme décrit dans le tableau ci-dessous|  
  
### <a name="to-add-the-sent-port"></a>Pour ajouter le port d’envoi  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi dans le **nom** , tapez un nom pour le port d’envoi.  
  
3.  Dans le **Transport** section, pour le **Type** zone, cliquez sur la liste déroulante, puis sélectionnez **fichier**.  
  
4.  Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.  
  
5.  Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.  
  
6.  Dans la boîte de dialogue Rechercher un dossier, déplacer vers le dossier que vous souhaitez envoyer des messages à partir de. Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si ce dossier n’existe pas, vous pouvez créer à l’aide de la **créer un nouveau dossier** commande.  
  
7.  Dans le **nom de fichier** , tapez **%MessageID%.txt**, puis cliquez sur **OK**.  
  
8.  Dans le **propriétés de Port d’envoi** boîte de dialogue, cliquez sur la liste déroulante pour le **pipeline d’envoi** zone, puis sélectionnez le pipeline d’envoi personnalisé.  
  
9. Dans le volet gauche, cliquez sur **filtres**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Sélectionnez **BTS. Opération**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **A4SWIFT_MRSRCompleted**.|  
    |**Grouper**|Sélectionnez **ou.**|  
    |**Propriété**|Sélectionnez **BTS. Opération**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **A4SWIFT_MRSRFailed**.|  
    |**Grouper**|Sélectionnez **ou**.|  
    |**Propriété**|Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **True**.|  
  
10. Cliquez sur **appliquer**, puis cliquez sur **OK.**  
  
11. Dans le **Ports d’envoi** volet, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.