---
title: Composants SSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passwords, synchronizing [SSO]
- SSO, components
- SSO, password synchronization
- SSO, sub-services
ms.assetid: e29e68df-f770-4220-a9f8-cb9323403017
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1111f1a0dfac47412ae28b58f93ddc51e1f562b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-components"></a><span data-ttu-id="73625-102">Composants de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="73625-102">SSO Components</span></span>
<span data-ttu-id="73625-103">Les sous-services du service d'authentification unique de l'entreprise sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="73625-103">The sub services of the Enterprise Single Sign-On (SSO) service are as follows:</span></span>  
  
-   <span data-ttu-id="73625-104">**Mappage.**</span><span class="sxs-lookup"><span data-stu-id="73625-104">**Mapping.**</span></span> <span data-ttu-id="73625-105">ce composant mappe le compte d'utilisateur du système Windows aux comptes d'utilisateur des systèmes principaux.</span><span class="sxs-lookup"><span data-stu-id="73625-105">This component maps the user account in the Windows system to the user accounts in the back-end systems.</span></span>  
  
-   <span data-ttu-id="73625-106">**Liste de choix.**</span><span class="sxs-lookup"><span data-stu-id="73625-106">**Lookup.**</span></span> <span data-ttu-id="73625-107">ce composant recherche les informations d'identification dans la base de données SSO du système principal.</span><span class="sxs-lookup"><span data-stu-id="73625-107">This component looks up the user credentials in the SSO database in the back-end system.</span></span> <span data-ttu-id="73625-108">Il s'agit du composant d'exécution SSO.</span><span class="sxs-lookup"><span data-stu-id="73625-108">This is the SSO runtime component.</span></span>  
  
-   <span data-ttu-id="73625-109">**Administration.**</span><span class="sxs-lookup"><span data-stu-id="73625-109">**Administration.**</span></span> <span data-ttu-id="73625-110">ce composant gère les applications associées et les mappages correspondants.</span><span class="sxs-lookup"><span data-stu-id="73625-110">This component manages the affiliate applications and the mappings for each affiliate application.</span></span>  
  
-   <span data-ttu-id="73625-111">**Clé secrète.**</span><span class="sxs-lookup"><span data-stu-id="73625-111">**Secret.**</span></span> <span data-ttu-id="73625-112">ce composant génère le secret principal et le distribue aux autres serveurs SSO du système.</span><span class="sxs-lookup"><span data-stu-id="73625-112">This component generates the master secret and distributes it to the other SSO servers in the system.</span></span> <span data-ttu-id="73625-113">Il n'est actif que sur le serveur SSO qui agit comme le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="73625-113">It is only active on the Single Sign-On server that is acting as the master secret server.</span></span>  
  
-   <span data-ttu-id="73625-114">**Synchronisation de mot de passe.**</span><span class="sxs-lookup"><span data-stu-id="73625-114">**Password Synchronization.**</span></span> <span data-ttu-id="73625-115">ce composant simplifie l'administration de la base de données SSO et synchronise les mots de passe au sein des annuaires d'utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="73625-115">This component simplifies administration of the SSO database, and keeps passwords in sync across user directories.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73625-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73625-116">See Also</span></span>  
 <span data-ttu-id="73625-117">[Serveur d’authentification unique](../core/sso-server.md) </span><span class="sxs-lookup"><span data-stu-id="73625-117">[SSO Server](../core/sso-server.md) </span></span>  
 [<span data-ttu-id="73625-118">L’installation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="73625-118">Installing SSO</span></span>](../core/installing-sso.md)