---
title: "Comment utiliser l’Assistant lien de rôle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- links [roles]
- Role Link Wizard [Orchestration Designer]
- roles, links
- Orchestration Designer, Role Link Wizard
- role links, Role Link Wizard [Orchestration Designer]
- links [roles], about links
ms.assetid: ddc33d87-c08d-4193-9483-4644ef302853
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d31abcc8fcc2bfaf1ebd641e1e52ad08d1c9c9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-role-link-wizard"></a>Comment utiliser l’Assistant lien de rôle
L'Assistant Lien de rôle vous permet de créer un nouveau lien de rôle ou d'en modifier un existant. Vous pouvez utiliser cet Assistant pour définir ou afficher le nom, le type et la restriction d'accès du lien de rôle ainsi que le rôle d'implémentation et le rôle d'utilisation qui composent le type de lien de rôle. Pour comprendre comment fonctionnent les liens de rôle, consultez [à l’aide des liens de rôle dans les Orchestrations](../core/using-role-links-in-orchestrations.md).  
  
 **Nom de lien de rôle**: le nom de lien de rôle est renseigné automatiquement et est le nom actuel d’un lien de rôle existant que vous configurez, ou un nom généré automatiquement si vous créez un lien de rôle. Dans les deux cas, vous pouvez le modifier.  
  
 **Type de lien de rôle**: vous pouvez sélectionner un type de lien de rôle existant ou créez-en un. Que vous configuriez un type de lien de rôle nouveau ou existant, vous pouvez spécifier comment votre orchestration participe au service.  
  
> [!NOTE]
>  Nous vous recommandons de créer le type de lien de rôle et le type de port associé avant de créer le lien de rôle afin de pouvoir utiliser un type existant pour sa définition. Pour plus d’informations, consultez [comment créer des liens de rôle dans les Orchestrations](../core/how-to-create-role-links-in-orchestrations.md).  
  
 **Utilisation du lien de rôle**: Si vous créez un lien de rôle de type, à la fois l’implémente et utilise les rôles sont créés automatiquement pour vous. Vous pouvez sélectionner le rôle qui reflète la manière dont votre orchestration participe au service. Une fois que vous avez complété toutes les étapes de l'Assistant, vous pouvez renommer les identificateurs de rôles ou supprimer un rôle afin de mieux vous adapter à votre implémentation. Un type de lien de rôle doit contenir l'un des types de rôles ou l'un de chaque type de rôle. Lorsque vous cliquez sur **OK**, les rôles non configurés sont créés correspondant à chaque nom. Vous pouvez également sélectionner des types de ports pour les rôles dans la fenêtre Types.  
  
> [!NOTE]
>  Si vous appelez l'Assistant Configuration du port pour créer un type de port pour votre type de lien de rôle et que vous souhaitez sélectionner un type de port précédemment défini, assurez-vous que les restrictions d'accès du type de port n'entrent pas en conflit avec les restrictions d'accès du type de lien de rôle.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de liens de rôle dans les Orchestrations](../core/using-role-links-in-orchestrations.md)