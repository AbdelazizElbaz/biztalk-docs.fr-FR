---
title: "Sauvegarde de la base de données A4SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up A4SWIFT database
- A4SWIFT database, backing up
ms.assetid: 53e46380-5be7-4d4c-b04c-d917ab40c07c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4102d459d5b579491f42747f1d3fe0dd3d381b71
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="backing-up-the-a4swift-database"></a><span data-ttu-id="84256-102">Sauvegarde de la base de données A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="84256-102">Backing Up the A4SWIFT Database</span></span>
<span data-ttu-id="84256-103">Vous devez sauvegarder régulièrement les bases de données dans votre système BizTalk Server et A4SWIFT afin de réduire les risques liés à une défaillance catastrophique.</span><span class="sxs-lookup"><span data-stu-id="84256-103">You should routinely back up the databases in your BizTalk Server and A4SWIFT system to lower the risks of a catastrophic failure.</span></span> <span data-ttu-id="84256-104">Ces bases de données incluent celles de votre système source de BizTalk Server et la base de données A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="84256-104">These databases include those in your BizTalk Server source system, and the A4SWIFT database.</span></span> <span data-ttu-id="84256-105">En plus de réduire les risques, cela sera vous permettent également à vider les fichiers d’historique A4SWIFT peuvent atteindre une taille importante.</span><span class="sxs-lookup"><span data-stu-id="84256-105">In addition to lowering risks, this will also enable you to purge A4SWIFT history files that can grow to a significant size.</span></span>  
  
 <span data-ttu-id="84256-106">Pour plus d’informations sur la sauvegarde des bases de données dans votre système source de BizTalk Server, consultez la rubrique « Sauvegarde et restauration de BizTalk Server bases de données » dans l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="84256-106">For more information about backing up the databases in your BizTalk Server source system, see the "Backing Up and Restoring BizTalk Server Databases" topic in the BizTalk Server Help.</span></span> <span data-ttu-id="84256-107">Cette rubrique décrit le travail de sauvegarde de BizTalk Server qui vous permet de sauvegarder les bases de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="84256-107">This topic describes the Backup BizTalk Server job that you use to back up BizTalk databases.</span></span>  
  
 <span data-ttu-id="84256-108">Pour plus d’informations sur la sauvegarde de la base de données A4SWIFT, consultez la rubrique « Comment revenir les personnalisé bases de données » dans l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="84256-108">For information about backing up the A4SWIFT database, see the "How to Back Up Custom Databases" topic in BizTalk Server Help.</span></span> <span data-ttu-id="84256-109">Cette rubrique décrit comment modifier le travail de sauvegarde de BizTalk Server pour la base de données A4SWIFT personnalisé.</span><span class="sxs-lookup"><span data-stu-id="84256-109">This topic describes how to modify the Backup BizTalk Server job to include the custom A4SWIFT database.</span></span>