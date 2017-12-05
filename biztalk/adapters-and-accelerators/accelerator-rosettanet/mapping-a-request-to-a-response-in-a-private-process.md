---
title: "Mappage d’une demande à une réponse dans un processus privé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, maps
- private processes, mapping requests
- private processes, customizing
- orchestrations, adding maps
- maps, adding to orchestrations
- maps, creating
- customizing private processes
- requests, mapping
- requests, private processes
ms.assetid: 5452c0a2-3a9b-43e7-bfa7-713eef0eab3b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 966ad6ad752c36be36b4013743eaba3af5434d0a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="mapping-a-request-to-a-response-in-a-private-process"></a>Mappage d’une demande à une réponse dans un processus privé
Cette rubrique décrit comment mapper un message de demande reçu par le processus de répondeur, à partir de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] processus répondeur public, un message de réponse qui peut être envoyé à la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processus de répondeur public.  
  
 Lorsqu’un répondeur reçoit un message de demande, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] achemine le message de demande à partir de l’orchestration de processus publics, à l’orchestration de processus privé, le programme de métier (LOB). Le répondeur nécessite le contenu du service de réponse à partir du programme métier pour générer un message de réponse RosettaNet à l’initiateur. De nombreux éléments dans le message de réponse sont remplies en utilisant les valeurs du message de demande. Par conséquent, vous pouvez incorporer un mappage dans l’orchestration de processus privé répondeur générer le message de contenu du service de réponse dans le format requis pour le programme LOB.  
  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK contient les exemples suivants que vous pouvez utiliser lorsque vous ajoutez un mappage à un répondeur privé-processus :  
  
-   [Exemple de mappage d’une demande 3A2 à une réponse 3A2](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)  
  
-   [Exemple de mappage d’une demande 3A4 à une réponse 3A4](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md)  
  
-   [Orchestration de PIPAutomation DoubleAction](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)  
  
-   [Orchestration de répondeur privé 3A4 avec une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)  
  
### <a name="to-create-the-map"></a>Pour créer le mappage  
  
1.  Démarrez **Microsoft Visual Studio 2012**.  
  
2.  Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet**.  
  
3.  Recherchez le dossier qui contient le projet BizTalk qui contient l’orchestration de processus privé auquel vous souhaitez ajouter la carte.  
  
4.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet, pointez sur **Ajouter**, puis cliquez sur **Nouvel élément**.  
  
5.  Dans la fenêtre Ajouter un nouvel élément, dans le **catégories** volet, cliquez sur **les fichiers de mappage**. Dans le volet Modèles, cliquez sur **carte**. Dans le **nom** zone, tapez un nom pour la carte, puis cliquez sur **ouvrir**.  
  
6.  Dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.  
  
7.  Dans la fenêtre de sélecteur de Type BizTalk, développez **schémas**, sélectionnez le schéma PIP pour le message de demande que vous souhaitez mapper à partir de, puis cliquez sur **OK**.  
  
8.  Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.  
  
9. Dans la fenêtre de sélecteur de Type BizTalk, développez **références**, développez **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, développez **schémas**, sélectionnez le schéma PIP pour le message de réponse auquel vous souhaitez mapper, puis cliquez sur **OK**.  
  
10. Cliquez sur le \< *schéma* \> nœud de schéma source, puis cliquez sur **développer le nœud d’arborescence**.  
  
11. Répétez l’étape 10 pour le schéma de destination.  
  
12. Dans le volet Schéma Source, cliquez et maintenez sur un champ que vous souhaitez mapper à un champ du schéma de destination. Faites glisser vers le nœud correspondant dans le volet Schéma de Destination.  
  
13. Répétez l’étape 12 pour tous les champs que vous devez effectuer un mappage entre les deux schémas.  
  
14. Validez et testez le mappage. Pour plus d’informations, consultez la rubrique « Compilation et test des cartes » dans l’aide de BizTalk Server.  
  
### <a name="to-add-the-map-to-the-orchestration"></a>Pour ajouter le mappage à l’orchestration  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur l’orchestration de processus privé.  
  
    > [!NOTE]
    >  Assurez-vous que l’orchestration comporte des références aux assemblys qui contiennent les schémas.  
  
2.  Dans la boîte à outils, cliquez sur le **transformer** mettre en forme et faites-le glisser vers le point dans l’orchestration à laquelle vous devez transformer le message de demande dans le message de réponse.  
  
    > [!NOTE]
    >  Pour obtenir un exemple de l’emplacement de la **transformer** mettre en forme, consultez l’orchestration PIP3A4PrivateResponder.odx. Il se trouve dans \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR. Cet exemple place le **transformer** sous la forme immédiatement la **IsActivityDoubleAction** forme. Pour plus d’informations, consultez [3 a 4 privé répondeur Orchestration à l’aide une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).  
  
    > [!NOTE]
    >  Pour obtenir un exemple de comment vous pouvez incorporer plusieurs mappages pour plusieurs adresses PIP, consultez [Orchestration Double Action PIPAutomation](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md).  
  
3.  Dans l’aire de conception d’orchestration, cliquez sur **ConstructMessage1**. Dans la fenêtre Propriétés, tapez un nom pour la forme et un nom pour le message doit être construite.  
  
4.  Dans l’aire de conception d’orchestration, cliquez sur **transformer**. Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (**...** ) à côté **nom de mappage**.  
  
5.  Dans la fenêtre de la transformation de Configuration, cliquez sur **mappage existant**et dans **nom de mappage complet**, cliquez sur la carte que vous venez de créer.  
  
6.  Sous **transformer**, cliquez sur **Source**. Cliquez sur la zone vide sous la variable et sélectionnez le nom du message de demande dans la liste déroulante.  
  
7.  Sous **transformer**, cliquez sur **Destination**. Cliquez sur la zone vide sous la variable et sélectionnez le nom du message de réponse dans la liste déroulante.  
  
8.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)