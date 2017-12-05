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
ms.openlocfilehash: bd62c1c965e814929537a62dc5d49be7e017ae3b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="known-issues-with-edi-migration"></a><span data-ttu-id="9a177-102">Problèmes connus avec la migration EDI</span><span class="sxs-lookup"><span data-stu-id="9a177-102">Known Issues with EDI Migration</span></span>
<span data-ttu-id="9a177-103">Cette rubrique décrit les problèmes connus avec la migration à partir du modèle d’adaptateur EDI/HIPAA dans [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9a177-103">This topic describes known issues with migration from the EDI/HIPAA adapter model in [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] to BizTalk Server.</span></span>  
  
## <a name="credential-information-not-migrated-for-a-file-send-port"></a><span data-ttu-id="9a177-104">Informations d'identification non migrées pour un port d'envoi FILE</span><span class="sxs-lookup"><span data-stu-id="9a177-104">Credential Information Not Migrated for a FILE Send Port</span></span>  
 <span data-ttu-id="9a177-105">Lors de la migration d'un port d'envoi à l'aide du type de transport FILE, les informations d'identification permettant d'accéder au dossier de fichiers lorsque l'hôte n'a pas accès au partage réseau ne sont pas migrées.</span><span class="sxs-lookup"><span data-stu-id="9a177-105">When migrating a send port using the FILE transport type, the credentials used to access the file folder when the host does not have access to the network share will not be migrated.</span></span> <span data-ttu-id="9a177-106">Après la migration, vous devez activer manuellement, ainsi qu’entrer le nom d’utilisateur et un mot de passe à utiliser dans le **authentification** page de la **propriétés du Transport FILE** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="9a177-106">After migration, you will need to manually enable credentials, and enter the user name and password to be used, on the **Authentication** page of the **FILE Transport Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a177-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a177-107">See Also</span></span>  
 <span data-ttu-id="9a177-108">[Dépannage des Solutions EDI et AS2](../core/troubleshooting-edi-and-as2-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="9a177-108">[Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md) </span></span>  
 [<span data-ttu-id="9a177-109">Utilitaires de migration EDI</span><span class="sxs-lookup"><span data-stu-id="9a177-109">EDI Migration Utilities</span></span>](../core/edi-migration-utilities.md)