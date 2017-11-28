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
# <a name="known-issues-with-edi-migration"></a><span data-ttu-id="4e72e-102">Problèmes connus avec la migration EDI</span><span class="sxs-lookup"><span data-stu-id="4e72e-102">Known Issues with EDI Migration</span></span>
<span data-ttu-id="4e72e-103">Cette rubrique décrit les problèmes connus relatifs à la migration du modèle d'adaptateur EDI/HIPAA dans [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e72e-103">This topic describes known issues with migration from the EDI/HIPAA adapter model in [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
## <a name="credential-information-not-migrated-for-a-file-send-port"></a><span data-ttu-id="4e72e-104">Informations d'identification non migrées pour un port d'envoi FILE</span><span class="sxs-lookup"><span data-stu-id="4e72e-104">Credential Information Not Migrated for a FILE Send Port</span></span>  
 <span data-ttu-id="4e72e-105">Lors de la migration d'un port d'envoi à l'aide du type de transport FILE, les informations d'identification permettant d'accéder au dossier de fichiers lorsque l'hôte n'a pas accès au partage réseau ne sont pas migrées.</span><span class="sxs-lookup"><span data-stu-id="4e72e-105">When migrating a send port using the FILE transport type, the credentials used to access the file folder when the host does not have access to the network share will not be migrated.</span></span> <span data-ttu-id="4e72e-106">Après la migration, vous devez activer manuellement, ainsi qu’entrer le nom d’utilisateur et un mot de passe à utiliser dans le **authentification** page de la **propriétés du Transport FILE** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4e72e-106">After migration, you will need to manually enable credentials, and enter the user name and password to be used, on the **Authentication** page of the **FILE Transport Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e72e-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e72e-107">See Also</span></span>  
 <span data-ttu-id="4e72e-108">[Dépannage des Solutions EDI et AS2](../core/troubleshooting-edi-and-as2-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="4e72e-108">[Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md) </span></span>  
 [<span data-ttu-id="4e72e-109">Utilitaires de Migration EDI</span><span class="sxs-lookup"><span data-stu-id="4e72e-109">EDI Migration Utilities</span></span>](../core/edi-migration-utilities.md)