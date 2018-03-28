---
title: Comment désactiver un mappage utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51c745dd-4d39-46e5-88bf-b803ae2e0a1b
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 93694ed8a3238be51b255bcad79122169461d885
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-disable-a-user-mapping"></a>Comment désactiver un mappage utilisateur
Vous pouvez désactiver un mappage utilisateur pour désactiver les opérations qui lui sont associées. Vous devez désactiver un mappage utilisateur avant de le supprimer.  
  
 Lorsque vous désactivez un mappage utilisateur, il apparaît comme (D) *\<domaine >\\< nom d’utilisateur\>* lorsque vous répertoriez les mappages utilisateur.  
  
### <a name="to-disable-a-user-mapping-using-the-administration-utility"></a>Pour désactiver un mappage utilisateur à l'aide de l'utilitaire d'administration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur **entrée**.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –disablemapping <domain>\<username><application name>`, où  *\<domaine >* correspond au domaine Windows pour le compte d’utilisateur,  *\<nom d’utilisateur >* est le nom d’utilisateur Windows pour lequel vous souhaitez désactiver le informations d’identification, et  *\<nom de l’application >* est le nom de l’application associée pour laquelle vous souhaitez supprimer le mappage utilisateur.  
  
### <a name="to-disable-a-user-mapping-using-the-client-utility"></a>Pour désactiver un mappage utilisateur à l'aide de l'utilitaire client  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur **entrée**.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient –disablemapping <application name>`, où  *\<nom de l’application >* est le nom de l’application associée pour laquelle vous souhaitez supprimer le mappage utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages SSO](../esso/sso-mappings.md)   
 [Gestion des Applications associées](../esso/managing-affiliate-applications.md)   
 [Gestion des mappages utilisateur](../esso/managing-user-mappings.md)