---
title: "Leçon 2 : Ajout d’un Port d’envoi de fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, flat files
- flat files, send ports
- creating, send ports
- send ports, creating
ms.assetid: 33dceb0d-85f5-4e19-820f-cd33b60cd32a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1370b4877c2e32055e2ee0a0aca1f922bd8668a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-adding-a-flat-file-send-port"></a>Leçon 2 : Ajout d’un Port d’envoi de fichier plat
Dans cette leçon, vous configurez le port d’envoi et de l’emplacement d’envoi. Le port d’envoi vous permet de définir comment vous souhaitez que les messages envoyés. Vous créez également un emplacement de dossier de fichiers pour les messages envoyés.  
  
### <a name="to-add-a-flat-file-send-port"></a>Pour ajouter un port d’envoi de fichier plat  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi dans le **nom** , tapez **MT103_FlatFile_SendPort**.  
  
3.  Dans le **Transport** section, pour le **Type** zone, cliquez sur la liste déroulante, puis sélectionnez **fichier**.  
  
4.  Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.  
  
5.  Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.  
  
6.  Dans la boîte de dialogue Rechercher un dossier, déplacer vers le  **\<lecteur > : \Labs** dossier, puis cliquez sur **créer un nouveau dossier**.  
  
7.  Créer un **sortant** dossier  **\<lecteur > : \Labs**, puis cliquez sur **OK**.  
  
8.  Dans le **nom de fichier** , tapez **%MessageID%.txt**, puis cliquez sur **OK**.  
  
9. Dans la boîte de dialogue Propriétés de Port d’envoi, cliquez sur la liste déroulante pour le **pipeline d’envoi** zone, puis sélectionnez **MT103SendPipeline**.  
  
10. Dans le volet gauche, cliquez sur **filtres**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Sélectionnez **BTS. ReceivePortName**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **MT103_XML_ReceivePort**.|  
  
11. Cliquez sur **appliquer**, puis cliquez sur **OK.**  
  
12. Dans le **Ports d’envoi** volet, avec le bouton droit **MT103_FlatFile_SendPort**, puis cliquez sur **Démarrer**.  
  
 Passez à [Module 5 : ajout d’un fichier plat emplacement de réception et Port d’envoi XML](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md).