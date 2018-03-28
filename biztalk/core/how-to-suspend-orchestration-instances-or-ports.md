---
title: Comment suspendre des Instances d’Orchestration ou des Ports | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, suspending
- instances, suspending
- suspending
- HAT, suspending orchestrations
- HAT, suspending pipelines
- suspending, ports
- suspending, orchestrations
- orchestrations, suspending
- HAT, suspending ports
- suspending, instances
- ports, suspending
ms.assetid: cacc7e58-7d3e-4d6b-adb0-618fdc4f0d89
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62d91c8d1e02b7283a430f7c82c572b6a989d108
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-suspend-orchestration-instances-or-ports"></a>Interruption des instances d'orchestration ou des ports
Vous pouvez suspendre des instances d'orchestration ou des ports à partir de la liste des résultats de la requête dans la console Administration de BizTalk Server.  
  
## <a name="prerequisites"></a>Configuration requise  
 Vous devez être connecté en tant que membre du groupe opérateurs BizTalk Server pour effectuer cette procédure.  
  
### <a name="to-suspend-orchestration-instances-or-ports"></a>Pour suspendre des instances d'orchestration ou des ports  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, puis cliquez sur le groupe BizTalk.  
  
3.  Dans le volet détails, cliquez sur le **nouvelle requête** onglet.  
  
4.  Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **en cours d’exécution des Instances de Service** dans la zone de liste déroulante.  
  
5.  Procédez de l'une des manières suivantes :  
  
    -   Pour interrompre une instance unique, dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez le **nom du Service** filtre et Ensuite, dans le **valeur** colonne, spécifiez le nom du service.  
  
    -   Pour suspendre les instances en bloc, dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez **grouper les résultats selon** puis, dans le **valeur** colonne, spécifiez le nom du service.  
  
6.  Cliquez sur **exécuter la requête**.  
  
7.  Dans la liste de résultats de requête, cliquez sur l’orchestration active ou le port que vous souhaitez suspendre, puis cliquez sur **suspendre l’Instance** ou **suspendre les Instances**.  
  
## <a name="see-also"></a>Voir aussi  
 [Examen des échecs relatifs aux orchestrations, aux ports et aux messages](../core/investigating-orchestration-port-and-message-failures.md)