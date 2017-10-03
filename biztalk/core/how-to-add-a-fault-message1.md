---
title: "L’ajout d’une erreur Message1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, adding messages
- fault messages, adding
- adding, fault messages
- faults, adding messages
ms.assetid: 9d21de6b-c1a5-46e9-a9dc-d6aa7b5fe34b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87ef85460f6ca6aea046ef9efff60fd198664cd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-fault-message"></a>Ajout d'un message d'erreur
Lorsque vous avez commencé par créer le port menant au système principal, il contenait une demande et une réponse. Vous devez ajouter une erreur pour capturer l'exception.  
  
### <a name="to-add-a-fault-message"></a>Pour ajouter un message d'erreur  
  
1.  Avec le bouton droit **opération de Port**, puis sélectionnez un **nouveau Message d’erreur**.  
  
     A **erreur** apparaît sous le **demande et réponse** dans le port.  
  
2.  Sur le **Vue Orchestration** de l’écran, cliquez sur **Messages**, puis sélectionnez **nouveau Message**.  
  
     Ceci crée le message Message_3, que vous pouvez affecter spécifiquement à l'erreur.  
  
3.  Avec le bouton droit **Message_3** pour accéder à la **propriétés** fenêtre.  
  
    1.  Définir le **Type de Message**.  
  
    2.  Sélectionnez **schéma**, puis sélectionnez à partir de **assembly de référence**.  
  
         Cette opération ouvre une **sélectionner le Type d’artefact** fenêtre.  
  
    3.  Faites défiler vers le bas et sélectionnez l'erreur complète.  
  
         Le nom est **BTS. SOAP_Envelope_1__1.fault**. Cliquez sur **OK** pour accepter la sélection et fermer la fenêtre.  
  
4.  Avec le bouton droit le **erreur** pour accéder à la **propriétés** fenêtre.  
  
    1.  Définir le **Type de Message**.  
  
    2.  Sélectionnez **schéma** puis sélectionnez à partir de **ref** assembly.  
  
         Cette opération ouvre une **sélectionner le Type d’artefact** fenêtre.  
  
    3.  Faites défiler vers le bas et sélectionnez l'erreur complète.  
  
         Le nom est **BTS. SOAP_Envelope_1__1.fault**.  
  
    4.  Cliquez sur **OK** pour accepter la sélection et fermer la fenêtre.  
  
         ![](../core/media/siebeladapter-17-exceptionhandling-addscope.gif "SiebelAdapter_17_ExceptionHandling_AddScope")  
  
5.  Une fois l'erreur nommée, vous définissez ce nom sur le type d'objet d'exception de CatchException.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling2.md)