---
title: "Création et la réparation des étapes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stages, repair
- stages, create
ms.assetid: 07d7ce7b-ed15-40a7-9c85-280a1d38985b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb87112775b9664badf319796e1a6243cf6eb082
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-repairing-stages"></a><span data-ttu-id="ad350-102">Création et la réparation des étapes</span><span class="sxs-lookup"><span data-stu-id="ad350-102">Creating and Repairing Stages</span></span>
<span data-ttu-id="ad350-103">La première étape dans les flux de travail peut être une étape de création ou de la réparation, autrement dit, les rôles qui ont une capacité définie comme créer ou réparer.</span><span class="sxs-lookup"><span data-stu-id="ad350-103">The first stage in any workflow can be either a Create or Repair stage, that is, roles that have a capability defined as create or repair.</span></span> <span data-ttu-id="ad350-104">Le message provient de la BizTalk MessageBox en tant qu’un message ayant échoué ou un [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur crée manuellement un message via le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms.</span><span class="sxs-lookup"><span data-stu-id="ad350-104">The message originates from the BizTalk MessageBox as a failed message or an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user manually creates a message through the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms.</span></span>  
  
 <span data-ttu-id="ad350-105">Le créateur de message d’origine ou le Réparateur est le premier signataire numérique du message et ajoute son propre signature numérique à la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire après avoir créé ou réparer le message.</span><span class="sxs-lookup"><span data-stu-id="ad350-105">The original message creator or repairer is the first digital signer of the message, and adds his or her digital signature to the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form after creating or repairing the message.</span></span> <span data-ttu-id="ad350-106">Cette première signature destiné à prouver l’identité de l’auteur du message ou réparateur mais verrouille également le contenu du message dans son état actuel.</span><span class="sxs-lookup"><span data-stu-id="ad350-106">This first signature not only proves the identity of the message creator or repairer, but also locks the contents of the message in its current state.</span></span> <span data-ttu-id="ad350-107">Si le message est modifié après la première signature, la pile de la signature numérique est interrompue et les avertissements sont affichés à l’utilisateur indiquant que les signatures numériques sur le formulaire ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="ad350-107">If the message is altered after the first signing, the digital signature stack is broken and warnings are shown to the user stating that the digital signatures on the form are invalid.</span></span>