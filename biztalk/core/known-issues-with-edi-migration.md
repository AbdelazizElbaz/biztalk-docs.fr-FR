---
title: "Problèmes connus avec Migration EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc5d0a7e-974d-4e3b-a406-412420779456
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b642c56151750232be3d17aa3f3cb3b8c858474c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-migration"></a>Problèmes connus avec la migration EDI
Cette rubrique décrit les problèmes connus relatifs à la migration du modèle d'adaptateur EDI/HIPAA dans [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
## <a name="credential-information-not-migrated-for-a-file-send-port"></a>Informations d'identification non migrées pour un port d'envoi FILE  
 Lors de la migration d'un port d'envoi à l'aide du type de transport FILE, les informations d'identification permettant d'accéder au dossier de fichiers lorsque l'hôte n'a pas accès au partage réseau ne sont pas migrées. Après la migration, vous devez activer manuellement, ainsi qu’entrer le nom d’utilisateur et un mot de passe à utiliser dans le **authentification** page de la **propriétés du Transport FILE** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des Solutions EDI et AS2](../core/troubleshooting-edi-and-as2-solutions.md)   
 [Utilitaires de Migration EDI](../core/edi-migration-utilities.md)