---
title: "Encodage de prise en charge étendue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93a40fa6-d0da-416e-97fb-675ddde3f005
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e36c3baff4ac33f2878295791bb3f6615c1b25d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extended-encoding-support"></a>Prise en charge du codage étendue
Par défaut, le HL7 reçoivent pipeline, BTAHL72X, prend uniquement en charge le codage ASCII. Cela signifie que tous les caractères dans un message d’entrée avec une valeur équivalente supérieure à 127 sont remplacées par « ? ». Il s’agit, car une valeur équivalente supérieure à 127 caractères ne sont pas représentés dans le jeu de caractères ASCII.  
  
 [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]prend en charge pour les deux encodages nouvelle :  
  
-   Europe occidentale  
  
-   UTF-8  
  
 Vous créez et créez un composant de pipeline personnalisé pour implémenter la prise en charge du codage étendue. Le composant de pipeline personnalisé utilise le BTAHL7 2.X désassembleur. Vous créez un emplacement de réception qui utilise le pipeline personnalisé pour traiter les messages. Pour tester l’emplacement de réception et un pipeline personnalisé, vous créez un port d’envoi qui utilise le 2.XSendPipeline BTAHL7.  
  
### <a name="to-create-a-custom-pipeline"></a>Pour créer un pipeline personnalisé  
  
1.  Dans [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)], ajoutez un nouveau **projet BizTalk Server vide**.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le nouveau projet, cliquez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue zone, ajoutez une nouvelle **Pipeline de réception**.  
  
4.  Dans la boîte à outils de pipeline, faites glisser le **BTAHL7 2.X désassembleur** à l’éditeur de pipeline et déposez-le sur le **désassembler** étape **Déposer ici** cible.  
  
    > [!NOTE]
    >  Si le désassembleur 2.7 BTAHL7 ne se trouve pas dans la boîte à outils, avec le bouton droit dans la boîte à outils, puis cliquez sur **choisir des éléments de**. Dans le **choisir des éléments de boîte à outils** boîte de dialogue le **composant de Pipeline BizTalk** onglet, sélectionnez le **BTAHL7 2.X désassembleur** case à cocher, puis cliquez sur **OK** .  
  
5.  Dans le volet Propriétés pour le **BTAHL7 2.X désassembleur**, à partir de la **codage de jeu de caractères** la liste déroulante, sélectionnez **Europe occidentale** ou **UTF8**codage.  
  
    > [!NOTE]
    >  HL7 prend uniquement en charge ASCII (la valeur par défaut), Europe et encodage UTF-8. Ne sélectionnez pas les autres options d’encodage HL7 ne prenant pas en charge les.  
  
6.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
7.  Déployez le projet.  
  
     Créer un nouvel emplacement de réception à continuer.  
  
### <a name="to-create-a-receive-location-that-uses-the-custom-pipeline"></a>Pour créer un emplacement de réception qui utilise le pipeline personnalisé  
  
1.  Sur le **Démarrer** menu, cliquez sur **programmes**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la console Administration de BizTalk Server, développez [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, développez l’application vous avez désigné pour votre assembly de pipeline (par défaut, **BizTalk Application 1**), avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **Unidirectionnel emplacement de réception**.  
  
3.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **pipeline de réception** liste déroulante, sélectionnez le nom personnalisé de pipeline que vous avez créé. (Il s’agit du nom de l’objet de pipeline personnalisé, pas le BTAHL7 de pipeline 2 X.)  
  
### <a name="to-create-a-send-port-to-test-the-receive-location-and-pipeline"></a>Pour créer un port d’envoi pour tester l’emplacement de réception et un pipeline  
  
1.  Sur le **Démarrer** menu, cliquez sur **programmes**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la console Administration de BizTalk Server, développez [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, développez l’application vous avez désigné pour votre assembly de pipeline (par défaut, **BizTalk Application 1**), avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **pipeline d’envoi** la liste déroulante, sélectionnez **BTAHL72XSendPipeline**.  
  
### <a name="to-test-the-receive-location-and-pipeline"></a>Pour tester l’emplacement de réception et un pipeline  
  
-   Supprimer un fichier contenant des caractères spéciaux et enregistré avec le même encodage spécifié dans le pipeline personnalisé dans l’emplacement indiqué dans l’emplacement de réception. Le fichier à l’emplacement de sortie doit conserver les caractères spéciaux.  
  
    > [!NOTE]
    >  Si vous essayez de traiter un fichier qui utilise un encodage non pris en charge (n’oubliez pas qu’uniquement ASCII, Europe et UTF-8 sont prises en charge), une erreur est consignée dans l’Observateur d’événements Application avec l’ID d’erreur : 5633.  
  
    > [!NOTE]
    >  Si vous testez un pipeline personnalisé configuré pour l’encodage UTF-8, les caractères de la marque d’ordre d’octet (BOM) doit être attaché au message que vous passez. Si vous testez un pipeline personnalisé configuré pour l’encodage Occidental, n’attachez pas les caractères de nomenclature.