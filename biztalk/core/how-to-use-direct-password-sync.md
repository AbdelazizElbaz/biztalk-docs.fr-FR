---
title: Comment utiliser la synchronisation de mot de passe directe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1334c2f-2020-46ea-a98c-f7688813e38c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6080589271d845432e875cb335a2ef354c9784ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-direct-password-sync"></a><span data-ttu-id="00b9d-102">Utilisation de la synchronisation de mot de passe directe</span><span class="sxs-lookup"><span data-stu-id="00b9d-102">How to Use Direct Password Sync</span></span>
<span data-ttu-id="00b9d-103">Cette version de l'authentification unique de l'entreprise inclut la fonctionnalité Synchronisation de mot de passe directe à partir de Windows.</span><span class="sxs-lookup"><span data-stu-id="00b9d-103">This version of Enterprise Single Sign-On includes the Direct Password Sync from Windows feature.</span></span> <span data-ttu-id="00b9d-104">Celle-ci vous évite de créer un adaptateur de synchronisation de mot de passe et met à jour le mot de passe, directement depuis Windows, dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="00b9d-104">This enables you to bypass a Password Sync Adapter and update the password in the SSO Database directly from Windows.</span></span>  
  
 <span data-ttu-id="00b9d-105">La synchronisation de mot de passe directe à partir de Windows est utile dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="00b9d-105">Direct Password Sync from Windows is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="00b9d-106">Le système de votre entreprise nécessite un mappage entre deux comptes Windows.</span><span class="sxs-lookup"><span data-stu-id="00b9d-106">Your enterprise system requires Windows to Windows mapping.</span></span>  
  
-   <span data-ttu-id="00b9d-107">Vous devez mettre à jour le mot de passe de l'utilisateur externe dans la base de données SSO directement lorsque le mot de passe de l'utilisateur Windows est modifié.</span><span class="sxs-lookup"><span data-stu-id="00b9d-107">You need to update the External User’s password in the SSO database directly when a password change occurs for the Windows user.</span></span> <span data-ttu-id="00b9d-108">Vous pouvez modifier le mot de passe sur le système principal (qui correspond à l'utilisateur externe) à l'aide d'autres mécanismes.</span><span class="sxs-lookup"><span data-stu-id="00b9d-108">You can change the password on the back-end system (that corresponds to the external user) by using other mechanisms.</span></span> <span data-ttu-id="00b9d-109">Par exemple, vous pouvez utiliser MIIS (Microsoft Identity Integration Server) pour mettre à jour les mots de passe dans RACF (Resource Access Control Facility) sur un macroordinateur IBM à l'aide de RACF Management Agent.</span><span class="sxs-lookup"><span data-stu-id="00b9d-109">For example, you can use Microsoft Identity Integration Server to update passwords in Resource Access Control Facility (RACF) on an IBM Mainframe using the RACF Management Agent.</span></span>  
  
### <a name="to-enable-direct-password-sync"></a><span data-ttu-id="00b9d-110">Pour activer la synchronisation de mot de passe directe</span><span class="sxs-lookup"><span data-stu-id="00b9d-110">To enable Direct Password Sync</span></span>  
  
1.  <span data-ttu-id="00b9d-111">Ouvrez l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="00b9d-111">Open Enterprise Single Sign-On.</span></span>  
  
2.  <span data-ttu-id="00b9d-112">Dans le volet d’étendue, cliquez sur **Applications associées**.</span><span class="sxs-lookup"><span data-stu-id="00b9d-112">In the scope pane, click **Affiliate Applications**.</span></span>  
  
3.  <span data-ttu-id="00b9d-113">Avec le bouton droit approprié **Application associée**.</span><span class="sxs-lookup"><span data-stu-id="00b9d-113">Right-click the appropriate **Affiliate Application**.</span></span>  
  
4.  <span data-ttu-id="00b9d-114">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="00b9d-114">Click **Properties**.</span></span>  
  
     <span data-ttu-id="00b9d-115">Le **propriétés des Applications associées** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="00b9d-115">The **Affiliate Applications Properties** dialog box appears.</span></span>  
  
5.  <span data-ttu-id="00b9d-116">Cliquez sur le **Options** onglet.</span><span class="sxs-lookup"><span data-stu-id="00b9d-116">Click the **Options** tab.</span></span>  
  
6.  <span data-ttu-id="00b9d-117">Sélectionnez le **synchronisation de mot de passe directe à partir de Windows** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="00b9d-117">Select the **Direct Password Sync from Windows** check box.</span></span>  
  
7.  <span data-ttu-id="00b9d-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="00b9d-118">Click **OK**.</span></span>