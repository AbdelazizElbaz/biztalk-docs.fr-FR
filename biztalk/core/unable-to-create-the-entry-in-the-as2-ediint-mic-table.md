---
title: "Impossible de créer l’entrée dans la table AS2 EDIINT MIC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1c75d70-e39e-4465-b32b-db646c059c9b
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c51cac2861fabaf8fc50269623130c90f3d445b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-create-the-entry-in-the-as2-ediint-mic-table"></a><span data-ttu-id="0d2f1-102">Impossible de créer l'entrée dans la table AS2 EDIINT MIC</span><span class="sxs-lookup"><span data-stu-id="0d2f1-102">Unable to create the entry in the AS2 EDIINT MIC table</span></span>
## <a name="details"></a><span data-ttu-id="0d2f1-103">Détails</span><span class="sxs-lookup"><span data-stu-id="0d2f1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d2f1-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="0d2f1-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0d2f1-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="0d2f1-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0d2f1-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0d2f1-106">Event ID</span></span>|-|  
|<span data-ttu-id="0d2f1-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="0d2f1-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0d2f1-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="0d2f1-108"> EDI</span></span>|  
|<span data-ttu-id="0d2f1-109">Composant</span><span class="sxs-lookup"><span data-stu-id="0d2f1-109">Component</span></span>|<span data-ttu-id="0d2f1-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="0d2f1-110">AS2 Engine</span></span>|  
|<span data-ttu-id="0d2f1-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="0d2f1-111">Symbolic Name</span></span>|<span data-ttu-id="0d2f1-112">AS2MicDataStoreCreateEntryError</span><span class="sxs-lookup"><span data-stu-id="0d2f1-112">AS2MicDataStoreCreateEntryError</span></span>|  
|<span data-ttu-id="0d2f1-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="0d2f1-113">Message Text</span></span>|<span data-ttu-id="0d2f1-114">Impossible de créer l'entrée dans la table AS2 EDIINT MIC.</span><span class="sxs-lookup"><span data-stu-id="0d2f1-114">Unable to create the entry in the AS2 EDIINT MIC table.</span></span> <span data-ttu-id="0d2f1-115">Ceci est peut-être dû à l'écriture dans la table de combinaisons de valeurs AS2-From, AS2-To et MessageID en double.</span><span class="sxs-lookup"><span data-stu-id="0d2f1-115">This could be caused by duplicate AS2-From, AS2-To and MessageID combinations being written to the table.</span></span>  <span data-ttu-id="0d2f1-116">Erreur : {0}</span><span class="sxs-lookup"><span data-stu-id="0d2f1-116">Error: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0d2f1-117">Explication</span><span class="sxs-lookup"><span data-stu-id="0d2f1-117">Explanation</span></span>  
 <span data-ttu-id="0d2f1-118">Cette erreur indique si des problèmes de connexion de base de données ou des clés de lignes existent déjà dans la table de base de données.</span><span class="sxs-lookup"><span data-stu-id="0d2f1-118">This error indicates either database connection problems or the row keys already exist in the database table.</span></span> <span data-ttu-id="0d2f1-119">Le message d'erreur complet doit fournir des informations sur la raison de l'échec de l'opération d'insertion.</span><span class="sxs-lookup"><span data-stu-id="0d2f1-119">The full error message should provide information as to why the insert operation failed.</span></span> <span data-ttu-id="0d2f1-120">Les entrées de la table étant supprimées une fois le MDN reçu (correctement ou non), cette erreur ne doit jamais se produire une fois le MDN reçu.</span><span class="sxs-lookup"><span data-stu-id="0d2f1-120">The entries in the table are removed after the MDN has been received (whether successful or failed), so this error should never happen after the MDN has been received.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0d2f1-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0d2f1-121">User Action</span></span>  
 <span data-ttu-id="0d2f1-122">Pour résoudre cette erreur, consultez le message d'erreur pour obtenir des informations sur la raison de l'échec de l'opération d'insertion.</span><span class="sxs-lookup"><span data-stu-id="0d2f1-122">To resolve this error, check the full error message for information about why the insert operation failed.</span></span> <span data-ttu-id="0d2f1-123">Dans SQL, dans la table EDIINT_MIC, déterminez s'il existe des doublons des combinaisons MessageID AS2-From et AS2-To.</span><span class="sxs-lookup"><span data-stu-id="0d2f1-123">In SQL, in the EDIINT_MIC table, determine whether there is duplicate AS2-From and AS2-To MessageID combinations.</span></span> <span data-ttu-id="0d2f1-124">Si c'est le cas, supprimez-les.</span><span class="sxs-lookup"><span data-stu-id="0d2f1-124">If so, remove them.</span></span>