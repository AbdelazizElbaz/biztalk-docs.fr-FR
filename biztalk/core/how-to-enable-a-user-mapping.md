---
title: Comment activer un mappage utilisateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enabling, user maps [SSO]
- maps [SSO], enabling
- managing [SSO maps], enabling
ms.assetid: 0f6448c9-944e-45f6-9436-87a4f3743498
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af4679d277a12335f8a9776695cd829473df460d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-a-user-mapping"></a>Comment activer un mappage utilisateur
Vous devez activer un mappage utilisateur avant d'utiliser le mappage dans le système d'authentification unique.  
  
 Lorsque vous activez un mappage utilisateur, il apparaît sous la forme (E)  **\<domaine >\\< nom d’utilisateur\>**  lorsque vous répertoriez les mappages utilisateur.  
  
 Notez que si vous avez configuré les informations d'identification à l'aide de la commande -setcredentials, le mappage est déjà activé.  
  
### <a name="to-enable-a-user-mapping-using-the-administration-utility"></a>Pour activer un mappage utilisateur à l'aide de l'utilitaire d'administration  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage-enablemapping \<domaine >\\< nom d’utilisateur\>\<nom de l’application >**, où  **\<domaine >** est domaine Windows pour le compte d’utilisateur,  **\<nom d’utilisateur >** est le nom d’utilisateur Windows pour lequel vous souhaitez activer les informations d’identification, et  **\<nom de l’application >**est le nom de l’application associée que vous souhaitez supprimer le mappage utilisateur, puis appuyez sur ENTRÉE.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-enable-a-user-mapping-using-the-client-utility"></a>Pour activer un mappage utilisateur à l'aide de l'utilitaire client  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient – enablemapping \<nom de l’application >**, où  **\<nom de l’application >** est le nom de l’application associée que vous souhaitez supprimer le mappage utilisateur.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer des mappages utilisateur](../core/how-to-create-user-mappings.md)   
 [Mappages SSO](../core/sso-mappings.md)   
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)