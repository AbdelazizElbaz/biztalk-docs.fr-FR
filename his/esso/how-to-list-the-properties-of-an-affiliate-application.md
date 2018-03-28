---
title: Comment afficher les propriétés d’une Application associée | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fac15775-39d0-470e-b9d2-21b2d02e1de7
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: e35f1f068f63d4db9738733bcada55047e81a19a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-list-the-properties-of-an-affiliate-application"></a>Comment afficher les propriétés d’une Application associée
Le **displayapp** commande affiche les informations suivantes sur l’application associée. Pour plus d’informations sur les propriétés d’une application associée, consultez [Applications associées SSO](../esso/sso-affiliate-applications.md).  
  
 Le système Single Sign-On (SSO) obtient ces informations à partir du fichier XML que vous avez utilisé pour mettre à jour de l’application associée. Pour plus d’informations, consultez [comment mettre à jour les propriétés d’une Application associée](../esso/how-to-update-the-properties-of-an-affiliate-application.md).  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-administration-utility"></a>Pour afficher les propriétés d'une application affiliée à l'aide de l'utilitaire d'administration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –displayapp <application name>`, où  *\<nom de l’application >* est le nom de l’application associée que vous souhaitez afficher les propriétés.  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-client-utility"></a>Pour afficher les propriétés d'une application affiliée à l'aide de l'utilitaire client  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est \< *lecteur d’installation*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient –displayapp <application name>`, où  *\<nom de l’application >* est le nom de l’application associée que vous souhaitez afficher les propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des mappages utilisateur](../esso/managing-user-mappings.md)   
 [Gestion des applications associées](../esso/managing-affiliate-applications.md)