---
title: "Développer des applications SAP à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF channel model, developing applications by using
ms.assetid: 1ce70c8b-5eeb-4585-97af-b0a7b4398dac
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13015cb042d26c946abfa3c99a4f67034b8d9708
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-sap-applications-using-the-wcf-channel-model"></a>Développer des applications SAP à l’aide du modèle de canal WCF
Vous pouvez utiliser la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de canal pour consommer le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] en envoyant des messages XML directement sur une instance de canal créée avec la liaison de SAP.  
  
 Un avantage de l’utilisation du modèle de canal WCF en utilisant les classes fortement typées et les méthodes que le modèle de service WCF expose est que le modèle de canal fournit un contrôle plus précis sur les opérations que vous effectuez sur le système SAP. Pourquoi ? Dans le modèle de canal WCF vous contrôler directement le contenu des messages que vous envoyez sur le canal.  
  
 Un autre avantage clé qui fournit un modèle de canal WCF sur le modèle de service WCF est prise en charge plus complète pour la diffusion en continu de données. En utilisant le modèle de canal WCF, vous pouvez effectuer :  
  
-   Nœud de message de diffusion en continu sur tous les messages échangés entre votre code et de la carte.  
  
-   Message-valeur du nœud de diffusion en continu sur les opérations SendIdoc et ReceiveIdoc.  
  
 Il s’agit, car dans le modèle de canal WCF vous contrôlez directement comment vous fournir le corps du message sur les messages que vous envoyez à l’adaptateur et comment vous consommez le corps du message sur les messages que vous recevez à partir de l’adaptateur.  
  
 En revanche, l’adaptateur ne fournit aucune prise en charge pour la diffusion en continu dans le modèle de service WCF. Étant donné que, dans le modèle de service WCF, le runtime WCF sérialise et désérialise les messages entre leurs XML et les représentations d’objets du code managé, une copie complète de la mémoire de chaque message que vous échangez avec l’adaptateur est effectuée.  
  
 Les sections de cette rubrique expliquent comment effectuer les opérations sur les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en utilisant le modèle de canal WCF.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble du modèle de canal WCF avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-channel-model-with-the-sap-adapter.md)  
  
-   [Créer un canal à l’aide de SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md)  
  
-   [Appeler des opérations sur le système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)  
  
-   [Réception d’opérations entrantes à partir du système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md) 
  
-   [Diffusion en continu IDOC de fichier plat dans SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)