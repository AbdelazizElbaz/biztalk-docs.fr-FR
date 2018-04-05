---
title: Tickets SSO | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tickets [SSO]
ms.assetid: acf01422-4696-4301-b85f-7026e792bb5c
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c0bf2f9c8278a71afd48da10195802169c3fad0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-tickets"></a>Tickets SSO
Dans un environnement d’entreprise, où un utilisateur interagit avec divers systèmes et applications, il est très probable que l’environnement ne gère pas le contexte de l’utilisateur par l’intermédiaire de plusieurs processus, les produits et les ordinateurs. Élément clé pour les fonctionnalités d'authentification unique, le contexte de l'utilisateur permet de vérifier l'initiateur de la demande d'origine. Pour remédier à ce problème, l'authentification unique de l'entreprise (SSO) génère un ticket SSO (différent d'un ticket Kerberos) que les applications peuvent utiliser pour obtenir les informations d'identification correspondant à l'utilisateur ayant initié la demande d'origine. Les tickets SSO ne sont pas activés par défaut. Pour plus d’informations sur l’activation des tickets, consultez [comment configurer les Tickets SSO](../core/how-to-configure-the-sso-tickets.md).  
  
 Le système d'authentification unique émet un ticket à la demande d'un utilisateur Windows authentifié. Il peut le faire pour l'utilisateur à l'origine de la demande ou pour un utilisateur distant. Un ticket contient le domaine chiffré et le nom d’utilisateur de l’utilisateur actuel et l’heure d’expiration du ticket. Par défaut, un ticket expire deux minutes après son émission. Les administrateurs de l'authentification unique peuvent modifier le délai d'expiration des tickets. Ils peuvent également définir l'expiration des tickets au niveau de l'application associée. Pour plus d’informations, consultez [comment configurer les Tickets SSO](../core/how-to-configure-the-sso-tickets.md).  
  
 Une fois qu'elle a vérifié l'identité de l'utilisateur à l'origine de la demande, l'application échange le ticket pour obtenir les informations d'identification de l'utilisateur ayant initié la demande. Les applications peuvent échanger les tickets du système d'authentification unique de deux manières :  
  
-   **Échanger uniquement.** Lorsqu'une application initie une demande d'échange d'un ticket, celle-ci doit contenir le nom de l'application associée à laquelle se connecter et le ticket lui-même. Seuls les administrateurs de l'application associée spécifique, les administrateurs des applications associées à authentification unique ou les administrateurs de l'authentification unique peuvent échanger un ticket. Vous devez utiliser **échanger uniquement** lorsqu’il existe un sous-système approuvé entre l’application qui a émis le ticket et l’application échange le ticket. Seul l'administrateur de l'application associée spécifiée peut échanger le ticket pour un utilisateur.  
  
-   **Valider et échanger.** Les tickets contiennent des informations sur l'utilisateur dont le système d'authentification unique recherche les informations d'identification. Dans ce cas, le service d'authentification unique vérifie que l'expéditeur du message d'origine et l'utilisateur du ticket sont identiques avant que le système n'échange le ticket. Les scénarios incluant l'adaptateur Microsoft BizTalk Server utilisent ce mécanisme.  
  
 Un administrateur de l'authentification unique peut désactiver l'expiration des tickets pour les applications associées individuelles. S'il s'agissait d'une alternative déconseillée dans les versions précédentes, la version présente prend en charge l'utilisation de l'expiration des tickets des applications associées individuelles. Cette option permet de définir l'expiration des tickets au niveau de l'application associée. Lorsque cette option n'est pas spécifiée, l'expiration des tickets au niveau global est utilisée.  
  
 Un administrateur des applications associées à authentification unique peut spécifier que les tickets sont autorisés et que la validation des tickets est requise pour les applications associées individuelles. En revanche, si l'administrateur de l'authentification unique spécifie au niveau du système d'authentification unique que la validation des tickets est requise, l'administrateur des applications associées à authentification unique ne peut pas désactiver cette option au niveau de l'application associée.  
  
> [!IMPORTANT]
>  Lorsque vous utilisez les tickets SSO, vous devez vous assurer que leur valeur d'expiration est suffisamment longue pour couvrir le délai entre le moment où ils sont émis et celui où ils sont échangés.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)