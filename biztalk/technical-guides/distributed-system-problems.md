---
title: "Distributed problèmes système | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 287b0adb-d5f9-4e47-80f8-0ba5d90c7864
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24abe471a66e8bc0724ad731388c5a0e7c07b573
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="distributed-system-problems"></a><span data-ttu-id="36dec-102">Problèmes de systèmes distribués</span><span class="sxs-lookup"><span data-stu-id="36dec-102">Distributed System Problems</span></span>
<span data-ttu-id="36dec-103">Les travaux de restauration ne sont pas connaissance des erreurs ou des problèmes sur les autres ordinateurs dans un système distribué de destination.</span><span class="sxs-lookup"><span data-stu-id="36dec-103">In a distributed destination system the restore jobs are not aware of errors or problems on the other computers.</span></span> <span data-ttu-id="36dec-104">Par exemple, supposons que l’ordinateur A restaurer la base de données de gestion BizTalk et la base de données des suivis BizTalk et ordinateur B restaure la base de données MessageBox de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="36dec-104">For example, suppose that computer A is restoring the BizTalk Management database and the BizTalk Tracking database, and computer B is restoring the BizTalk MessageBox database.</span></span> <span data-ttu-id="36dec-105">Les deux ordinateurs restaurer correctement les jeux de sauvegarde 1 à 25.</span><span class="sxs-lookup"><span data-stu-id="36dec-105">Both computers successfully restore backup sets 1 through 25.</span></span> <span data-ttu-id="36dec-106">Ensemble 26, toutefois, comporte un fichier de sauvegarde de journal endommagé de la base de données MessageBox de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="36dec-106">Set 26, however, has a corrupted log backup file of the BizTalk MessageBox database.</span></span> <span data-ttu-id="36dec-107">Ordinateur A restaure ses bases de données correctement, mais l’ordinateur B échoue restaurer le fichier endommagé.</span><span class="sxs-lookup"><span data-stu-id="36dec-107">Computer A restores its databases correctly but computer B fails to restore the corrupted file.</span></span>  
  
 <span data-ttu-id="36dec-108">Dans ce cas, force une sauvegarde complète sur le système source.</span><span class="sxs-lookup"><span data-stu-id="36dec-108">In this situation, force a full backup on the source system.</span></span> <span data-ttu-id="36dec-109">Poursuivre l’exemple ci-dessus, supposons que le problème a été identifiée et une sauvegarde complète a été créée pour le jeu de 35.</span><span class="sxs-lookup"><span data-stu-id="36dec-109">Continuing the example above, assume that the problem was diagnosed and a full backup was created for set 35.</span></span> <span data-ttu-id="36dec-110">Ordinateur A puis restaurations jeux 26 à 34, car il n’est pas conscient du problème sur l’ordinateur B. ordinateur B échouera jusqu'à ce qu’il voit 35 du jeu de sauvegarde complète et 36 (n’oubliez pas que ceci doit toujours être une sauvegarde de journal complet suivantes pour un jeu soit restauration du jeu de sauvegarde de journal suivante d).</span><span class="sxs-lookup"><span data-stu-id="36dec-110">Computer A then restores sets 26 to 34, because it is not aware of the problem on Computer B. Computer B will fail until it sees full backup set 35 and subsequent log backup set 36 (remember that there must always be one subsequent complete log backup for a set to be restored).</span></span> <span data-ttu-id="36dec-111">Lorsque les jeux de 35 et 36 arrive sur l’ordinateur B, il se corrigera d’elle-même à l’aide de 35.</span><span class="sxs-lookup"><span data-stu-id="36dec-111">When sets 35 and 36 arrive on computer B, it will repair itself using 35.</span></span> <span data-ttu-id="36dec-112">Une fois la réparation terminée, les ordinateurs A et B seront synchronisés.</span><span class="sxs-lookup"><span data-stu-id="36dec-112">After the repair is complete, computer A and B will be in sync.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36dec-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36dec-113">See Also</span></span>  
 [<span data-ttu-id="36dec-114">Résolution des problèmes d’envoi de journaux</span><span class="sxs-lookup"><span data-stu-id="36dec-114">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)