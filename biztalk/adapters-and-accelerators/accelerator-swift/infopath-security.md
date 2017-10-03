---
title: "InfoPath sécurité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, InfoPath forms
- InfoPath forms, security
ms.assetid: 6ed7b5cc-9801-45a5-8fdb-e5d56dd36435
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ec5478af7c404840bf1c5c80be5520e405bd26a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="infopath-security"></a>Sécurité d’InfoPath
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 utilise des Signatures XML pour vous permettre de signer numériquement un formulaire à l’aide d’un certificat numérique. Les Signatures XML définit une norme pour les signatures numériques basé sur XML que vous utilisez pour vous aider à sécuriser les données contenues dans les documents XML. Les Signatures XML est une norme régie par le World Wide Web Consortium (W3C).  
  
 Une signature numérique est un cachet électronique et sécurisé de l’authentification d’une macro ou un document. Lors de la signature numérique d’un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire, l’instance XML par le formulaire est « estampillée » avec une signature numérique (signature public résumé des données de clé et signé est écrite dans un nœud dédié dans le code XML). Cette signature confirme que le document XML du signataire et qu’il n’a pas été modifié. [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]Fournit la signature vérifiable, non répudiée, signature partielle, cosigning et contresignant prise en charge améliorée de signature numérique.  
  
 Les solutions SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms générés avec l’utilitaire FormGenerator fournie par A4SWIFT utilisent la méthode countersigning de la signature numérique pour vous permettre de signatures de countersigners pour être empilées les unes sur les autres. Cette pile signature countersigning modélise le processus humains de création ou modification d’un message SWIFT, incluant le message révisé et approuvé par un ou plusieurs réviseurs et les approbateurs et enfin envoyer ce message uniquement une fois toutes les étapes dans un flux de travail ont approuvé.  
  
 Réparateurs, les réviseurs ou les approbateurs signer le message qu’ils approuvent ou rejettent. La signature signifie l’authenticité de la réponse et ne signifie pas nécessairement une décision « acceptée ».  
  
 Lorsque la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire est envoyé, il vérifie les messages de validité et que l’utilisateur de la signature du formulaire est le bon rôle.  
  
 Si le message est rejeté à tout moment dans un flux de travail (en plus de réparation), le message est envoyé à la phase de réparation. Si le message est rejeté au stade réparateur ou créateur, Message Repair et New Submission envoie le message à l’instance d’orchestration Message Repair et New Submission avec propriétés spécifiques de marquer le message comme étant rejeté.  
  
 Cette section décrit la façon dont Message Repair et New Submission gère les signatures numériques basées sur les fonctionnalités définies pour un rôle. La combinaison de rôle et la fonction est appelée une « phase » dans le flux de travail.  
  
> [!NOTE]
>  Le rôle « créer » est limité à un créateur d’unique entre tous les services.  
  
 Contenu de cette section :  
  
-   [Création et la réparation des étapes](../../adapters-and-accelerators/accelerator-swift/creating-and-repairing-stages.md)  
  
-   [Recomposition la phase de vérification](../../adapters-and-accelerators/accelerator-swift/rekey-verification-stage.md)  
  
-   [Étape d’approbation](../../adapters-and-accelerators/accelerator-swift/approval-stage.md)  
  
-   [Distribuer des certificats numériques](../../adapters-and-accelerators/accelerator-swift/distributing-digital-certificates.md)