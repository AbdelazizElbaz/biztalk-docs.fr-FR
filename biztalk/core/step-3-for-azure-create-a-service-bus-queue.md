---
title: "Étape 3 (pour Azure) : Créer une file d’attente du Bus de Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7192c3c-4ebf-49c4-b8ce-46a6e9fb5f4a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d55b3222798edb245000cdde8de52565c39758a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-for-azure-create-a-service-bus-queue"></a>Étape 3 (pour Azure) : Créer une file d’attente du Bus de Service
Dans cette rubrique, vous allez créer une file d’attente Service Bus à laquelle sera envoyée la commande client X12 après avoir été traitée et transformée à l’aide de l’accord EDI.  
  
### <a name="to-create-a-service-bus-queue"></a>Pour créer une file d’attente Service Bus  
  
1.  Se connecter à la [portail de gestion Windows Azure CTP](http://go.microsoft.com/fwlink/p/?LinkId=202886) à l’aide de votre compte Microsoft.  
  
2.  Sur le côté inférieur gauche de la page, cliquez sur **AppFabric**.  
  
3.  Développez les services dans l’arborescence à gauche, développez votre abonnement, puis cliquez sur un espace de noms que vous devez avoir déjà créé. Si vous n’avez pas déjà un espace de noms, consultez [Comment : créer ou modifier un Namespace de Service Windows Azure CTP](http://msdn.microsoft.com/library/windowsazure/hh697699.aspx).  
  
4.  Pour créer une file d’attente, cliquez sur **nouvelle file d’attente** à partir de la **gérer les entités** catégorie à partir de la barre d’outils en haut de la page.  
  
5.  Dans le **nouvelle file d’attente** boîte de dialogue, entrez un nom pour la file d’attente. Pour ce didacticiel, entrez le nom du `queueordersedi`, puis cliquez sur **OK**. Vous avez spécifié ce nom dans le cadre de l’accord EDI que vous avez créé dans [étape 2 (pour Azure) : création d’un accord EDI](../core/step-2-for-azure-create-an-edi-agreement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)