---
title: "Se connecter au système Siebel dans Visual Studio à l’aide d’ajouter une référence de Service d’adaptateur plug-in | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d27121be-6407-4bb6-acb5-37dc8a3785c0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 696e91d689bfc7bc058ce0c512e8fa09b91b18a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-the-siebel-system-in-visual-studio-using-add-adapter-service-reference-plug-in"></a>Se connecter au système Siebel dans Visual Studio à l’aide d’ajouter une référence de Service d’adaptateur plug-in
Pour vous connecter à un système Siebel à l’aide du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] dans une solution de programmation .NET, vous devez utiliser le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. Cette rubrique fournit des instructions sur l’utilisation de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
## <a name="connecting-to-a-siebel-system-using-add-adapter-service-reference-plug-in"></a>Connexion à un système Siebel à l’aide d’ajouter une référence de Service d’adaptateur plug-in  
 Les étapes suivantes pour vous connecter à un système Siebel à l’aide du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-connect-to-a-siebel-system"></a>Pour vous connecter à un système Siebel  
  
1.  Pour se connecter à l’aide de le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dans une solution BizTalk :  
  
    1.  Créez un projet BizTalk à l’aide [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
    2.  Cliquez sur le projet dans l’Explorateur de solutions, puis cliquez sur **ajouter une référence de Service de carte**. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] s’ouvre.  
  
2.  À partir de la **sélectionner une liaison** la liste déroulante, sélectionnez **siebelBinding**, puis cliquez sur **configurer**.  
  
3.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur**.  
  
4.  Spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système Siebel.  
  
5.  Cliquez sur le **propriétés URI** onglet et spécifier des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], consultez [créer l’URI de connexion système Siebel](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  
  
    > [!NOTE]
    >  Si les paramètres de connexion contiennent des caractères réservés, vous devez les spécifier en tant que-est dans le **propriétés URI** onglet, autrement dit, sans utiliser de caractères d’échappement. Toutefois, si vous spécifiez l’URI directement dans le **configurer un URI** champ et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
6.  Cliquez sur le **propriétés de liaison** onglet et spécifiez des valeurs pour les propriétés de liaison, si elle existe, requis par les opérations que vous souhaitez cibler. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
7.  Cliquez sur **OK**.  
  
8.  Cliquez sur **Se connecter**. Une fois que la connexion est établie, l’état de connexion s’affiche en tant que **connecté**.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immédiatement après la connexion est établie. L’interface utilisateur graphique est identique pour les [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
     ![Consume Adapter Service connecté de boîte de dialogue](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")  
  
     Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] affiche les différents nœuds contenant plusieurs opérations qui peuvent être effectuées sur le système Siebel. Par exemple, le **des objets métier** nœud contient tous les objets métier et les composants d’entreprise qui peuvent être appelées sur le système Siebel. De même, la **Services professionnels** nœud contient tous les services d’entreprise dans le système Siebel vous connecté. Pour plus d’informations sur ces nœuds, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).