---
title: Serveur de secret principal | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, about Master Secret server
- Master Secret server, SSO
- SSO, encryption key
- Master Secret server, encryption key
- SSO, Master Secret server
ms.assetid: 93685a19-6c27-45db-bfc1-957574362687
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d02d5608546e86801bfc4a2281c42f902594e79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="master-secret-server"></a>Serveur de secret principal
Le serveur de secret principal correspond au serveur d'authentification unique de l'entreprise qui contient le secret principal (clé de chiffrement). Le serveur de secret principal génère le secret principal quand un administrateur SSO le demande. Ce serveur enregistre le secret principal chiffré dans le Registre. Seuls les administrateurs de l'authentification unique peuvent accéder au secret principal.  
  
 Les autres serveurs d'authentification unique vérifient si le secret principal a changé toutes les 30 secondes. Dans l'affirmative, ils le lisent de manière sécurisée. Sinon, ils continuent d'utiliser le secret principal déjà mis en mémoire cache. Le service d'authentification unique utilise le secret principal pour chiffrer et déchiffrer les informations d'identification des utilisateurs.  
  
 Vous ne pouvez utiliser le système d'authentification unique qu'une fois le serveur de secret principal configuré et le secret principal généré par un administrateur de l'authentification unique. Le serveur de secret principal génère le secret principal lors de la configuration. Seuls les administrateurs de l'authentification unique sont autorisés à le générer. Un administrateur de l'authentification unique doit configurer le serveur de secret principal et la base de données SSO pour qu'une application puisse utiliser le service d'authentification unique.  
  
> [!IMPORTANT]
>  Une fois le secret principal généré, il est fortement recommandé de le sauvegarder et de le stocker dans un emplacement sécurisé.  
  
 Lorsqu'un administrateur de l'authentification unique doit régénérer le secret principal (par exemple, s'il souhaite modifier le secret principal périodiquement), le serveur de secret principal stocke l'ancien secret principal et le nouveau secret principal. Le serveur de secret principal passe en revue les mappages, les déchiffre à l'aide de l'ancien secret principal et les chiffre à nouveau à l'aide du nouveau secret principal.  
  
 Si le serveur de secret principal échoue, les opérations d'exécution déjà en cours continuent d'être exécutées, mais les serveurs d'authentification unique ne peuvent plus chiffrer les nouvelles informations d'identification.  
  
> [!IMPORTANT]
>  Il ne peut y avoir qu'un serveur de secret principal dans votre système SSO. Par conséquent, il est fortement recommandé de mettre celui-ci en cluster. Pour plus d’informations, consultez [mise en Cluster du serveur de secret principal](../core/how-to-cluster-the-master-secret-server1.md).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’authentification unique](../core/using-sso.md)