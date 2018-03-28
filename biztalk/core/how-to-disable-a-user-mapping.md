---
title: Comment désactiver un mappage utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disabling, maps
- managing [SSO maps], disabling
- maps [SSO], disabling
ms.assetid: 9b6eaff2-674b-49f7-8d5c-3e040a7dc7f8
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b17ab68356d5d39f3f839f736261d4a7ef79c78
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-disable-a-user-mapping"></a>Comment désactiver un mappage utilisateur
Vous pouvez désactiver un mappage utilisateur pour désactiver les opérations qui lui sont associées. Vous devez désactiver un mappage utilisateur avant de le supprimer.  
  
 Lorsque vous désactivez un mappage utilisateur, il apparaît comme (D) *\<domaine\>\\< nom d’utilisateur\>* lorsque vous répertoriez les mappages utilisateur.  
  
### <a name="to-disable-a-user-mapping-using-the-administration-utility"></a>Pour désactiver un mappage utilisateur à l'aide de l'utilitaire d'administration  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage-disablemapping  *\<domaine\>*\\*\<nom d’utilisateur\> \<nom de l’application\>***, où *\<domaine\>* correspond au domaine Windows pour le compte d’utilisateur, et *\<nom d’utilisateur\>* est le nom d’utilisateur Windows pour lequel vous souhaitez désactiver les informations d’identification, et *\<nom de l’application\>* est le nom de l’application associée que vous souhaitez supprimer le mappage utilisateur.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-disable-a-user-mapping-using-the-client-utility"></a>Pour désactiver un mappage utilisateur à l'aide de l'utilitaire client  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type ** ssoclient – disablemapping *\<nom de l’application\>***, où *\<nom de l’application\>* est le nom de l’application associée que vous souhaitez supprimer le mappage utilisateur.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages SSO](../core/sso-mappings.md)   
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)