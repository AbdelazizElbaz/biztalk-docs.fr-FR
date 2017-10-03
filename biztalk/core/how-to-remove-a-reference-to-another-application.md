---
title: "Comment supprimer une référence à une autre Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: applications, references
ms.assetid: cc867706-7c56-4386-b7ec-9fd7cf6c83a4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de51adb1a9c42874025527ad458ecb6e3c311b3f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-reference-to-another-application"></a>Suppression d'une référence à une autre application
La présente rubrique explique comment supprimer une référence d'une application à une autre application à l'aide de la console Administration de BizTalk Server. Vous supprimez une référence lorsque vous n'avez plus besoin, dans l'application actuelle, d'un artefact existant déjà dans une autre application du même groupe BizTalk. Pour plus d’informations sur l’ajout de références, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).  
  
 Dans l'application actuelle, si des artefacts utilisent toujours des artefacts dans l'application référencée, l'opération de suppression de la référence échouera.  
  
> [!CAUTION]
>  Toute application BizTalk Server contient automatiquement une référence à l'application BizTalk.System. Ceci est dû au fait que les artefacts que contient BizTalk.System sont utilisés par toutes les applications BizTalk. Vous ne devez jamais supprimer une référence à l'application BizTalk.System. Votre application risquerait sinon de ne plus fonctionner correctement.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-remove-a-reference-to-another-application"></a>Pour supprimer une référence à une autre application  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, cliquez sur l’application à partir de laquelle vous souhaitez supprimer une référence (celle qui fait référence à une autre application), puis cliquez sur **propriétés**.  
  
3.  Dans le volet gauche de la page de propriétés, cliquez sur **références**.  
  
4.  Dans le volet droit, cliquez sur l’application que vous ne souhaitez plus faire référence à partir de cette application, cliquez sur **supprimer**, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)