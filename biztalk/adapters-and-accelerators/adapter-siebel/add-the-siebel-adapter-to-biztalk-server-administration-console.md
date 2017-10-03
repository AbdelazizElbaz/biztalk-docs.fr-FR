---
title: "Ajouter l’adaptateur Siebel à la Console Administration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b64d0bdc-ac83-46c9-b27d-625088a013d3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebb4a946c9fd987c1a97fa24a9b50d3cdf2f7d18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="add-the-siebel-adapter-to-biztalk-server-administration-console"></a>Ajouter l’adaptateur Siebel à la Console Administration de BizTalk Server
Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] peut être utilisé en tant qu’un port WCF-Custom ou WCF-Siebel dans BizTalk. Si vous souhaitez utiliser le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] via un port personnalisé WCF, vous n’avez pas besoin ajouter le port WCF-Custom à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, car le port WCF-Custom est ajouté à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration par défaut. Toutefois, si vous souhaitez utiliser le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] via un port WCF-Siebel, vous devez d’abord ajouter l’adaptateur WCF-Siebel à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
 Cette rubrique fournit des instructions sur l’ajout de l’adaptateur WCF-Siebel à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
> [!IMPORTANT]
>  Vous ne devez pas effectuer ces tâches si vous souhaitez configurer un port personnalisé WCF pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
## <a name="add-the-siebel-adapter"></a>Ajouter l’adaptateur Siebel  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez le **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **cartes**.  
  
3.  Avec le bouton droit **cartes**, pointez sur **nouveau**, puis cliquez sur **carte**.  
  
     ![Ajouter un adaptateur](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")  
  
4.  Dans le **propriétés de la carte** boîte de dialogue, spécifiez un nom pour l’adaptateur et à partir de la **carte** liste, sélectionnez **WCF-Siebel**.  
  
     ![Ajouter WCF &#45; L’adaptateur Siebel à la console BizTalk](../../adapters-and-accelerators/adapter-siebel/media/6d39b874-2233-452a-81ef-d93274b0784c.gif "6d39b874-2233-452a-81ef-d93274b0784c")  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)