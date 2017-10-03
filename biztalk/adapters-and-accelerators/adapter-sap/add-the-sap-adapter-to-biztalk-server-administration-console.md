---
title: "Ajouter l’adaptateur SAP à la Console Administration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95fc925d-0aac-4f0d-a19d-ad27469e4b3c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19870e69dc502f9635f34b578c2853aaf8897e00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="add-the-sap-adapter-to-biztalk-server-administration-console"></a>Ajouter l’adaptateur SAP à la Console Administration de BizTalk Server
Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peut être utilisé en tant qu’un port WCF-Custom ou WCF-SAP dans BizTalk. Si vous souhaitez utiliser le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] via un port personnalisé WCF, vous n’avez pas besoin ajouter le port WCF-Custom à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, car le port WCF-Custom est ajouté à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration par défaut. Toutefois, si vous souhaitez utiliser le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] via un port WCF SAP, vous devez d’abord ajouter l’adaptateur WCF-SAP pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
 Cette rubrique fournit des instructions sur l’ajout de l’adaptateur WCF-SAP pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
> [!IMPORTANT]
>  Vous ne devez pas effectuer ces tâches si vous souhaitez configurer un port personnalisé WCF pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="add-the-sap-adapter"></a>Ajouter l’adaptateur SAP  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez le **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **cartes**.  
  
3.  Avec le bouton droit **cartes**, pointez sur **nouveau**, puis cliquez sur **carte**.  
  
     ![Ajouter un adaptateur](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")  
  
4.  Dans le **propriétés de la carte** boîte de dialogue, spécifiez un nom pour l’adaptateur et à partir de la **carte** liste, sélectionnez **WCF SAP**.  
  
     ![Ajouter un adaptateur SAP à BizTalk](../../adapters-and-accelerators/media/a1235b38-ab93-4233-924d-42710540b951.gif "a1235b38-ab93-4233-924d-42710540b951")  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)