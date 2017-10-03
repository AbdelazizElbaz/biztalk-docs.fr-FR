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
# <a name="creating-and-repairing-stages"></a>Création et la réparation des étapes
La première étape dans les flux de travail peut être une étape de création ou de la réparation, autrement dit, les rôles qui ont une capacité définie comme créer ou réparer. Le message provient de la BizTalk MessageBox en tant qu’un message ayant échoué ou un [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur crée manuellement un message via le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms.  
  
 Le créateur de message d’origine ou le Réparateur est le premier signataire numérique du message et ajoute son propre signature numérique à la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire après avoir créé ou réparer le message. Cette première signature destiné à prouver l’identité de l’auteur du message ou réparateur mais verrouille également le contenu du message dans son état actuel. Si le message est modifié après la première signature, la pile de la signature numérique est interrompue et les avertissements sont affichés à l’utilisateur indiquant que les signatures numériques sur le formulaire ne sont pas valides.