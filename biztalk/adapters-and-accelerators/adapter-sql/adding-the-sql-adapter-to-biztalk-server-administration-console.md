---
title: "Ajout de l’adaptateur SQL à la Console Administration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd974f28-c9cb-46de-95be-83716231ebcd
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3510fb31bffe4c5823593fac34d5d5f1d5849c65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-the-sql-adapter-to-biztalk-server-administration-console"></a>Ajout de l’adaptateur SQL à la Console Administration de BizTalk Server
Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut être utilisé en tant qu’un port WCF-Custom ou WCF-SQL dans BizTalk. Si vous souhaitez utiliser le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] via un port personnalisé WCF, vous n’avez pas besoin ajouter le port WCF-Custom à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, car le port WCF-Custom est ajouté à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration par défaut. Toutefois, si vous souhaitez utiliser le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] via un port WCF-SQL, vous devez d’abord ajouter l’adaptateur WCF-SQL pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
 Cette rubrique vous montre comment ajouter l’adaptateur WCF-SQL pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
> [!IMPORTANT]
>  Vous n’avez pas besoin de suivre ces étapes si vous souhaitez configurer un port personnalisé WCF pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## <a name="add-the-sql-adapter"></a>Ajouter l’adaptateur SQL  
  
1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Développez le **groupe BizTalk**, développez **paramètres de plateforme**, puis sélectionnez **cartes**.  
  
3.  Avec le bouton droit **cartes**, pointez sur **nouveau**, puis sélectionnez **carte**.  
  
     ![Ajouter un adaptateur](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")  
  
4.  Dans le **propriétés de la carte** boîte de dialogue, entrez un nom pour la carte et de la **carte** liste, sélectionnez **WCF-SQL**.  
  
     ![Ajouter WCF &#45; Adaptateur SQL à BizTalk](../../adapters-and-accelerators/adapter-sql/media/4c6e2650-5d3a-4de8-a60a-a136d93a6fcf.gif "4c6e2650-5d3a-4de8-a60a-a136d93a6fcf")  
  
5.  Sélectionnez **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)