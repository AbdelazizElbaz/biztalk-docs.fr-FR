---
title: Configuration de la programmation carte | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e5fef6c-6928-42e7-9a1f-42b5bd769937
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e908b3ac79970b917e1e7964868b3b9d5bd852d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-programming-configuration"></a><span data-ttu-id="67684-102">Configuration de programmation de carte</span><span class="sxs-lookup"><span data-stu-id="67684-102">Adapter Programming Configuration</span></span>
<span data-ttu-id="67684-103">Chaque type d'adaptateur de synchronisation de mot de passe exige une configuration différente, selon le système non-Windows pour lequel vous concevez l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="67684-103">Every type of password sync adapter has different configuration requirements, depending on what non-Windows system you design the adapter for.</span></span> <span data-ttu-id="67684-104">À l'instar des applications associées, vous pouvez utiliser le magasin de configuration du service d'authentification unique de l’entreprise pour stocker les propriétés de configuration de manière centralisée et plus sécurisée.</span><span class="sxs-lookup"><span data-stu-id="67684-104">Like affiliate applications, you can use the Enterprise Single Sign-On configuration store to store configuration properties centrally and more securely.</span></span>  
  
 <span data-ttu-id="67684-105">Comme il le ferait avec d'autres applications de stockage de configuration, un administrateur peut utiliser l'interface utilisateur de gestion de l'authentification unique de l'entreprise pour localiser et lire un fichier XML décrivant les propriétés de configuration de votre adaptateur.</span><span class="sxs-lookup"><span data-stu-id="67684-105">As with other configuration store applications, an administrator can use the Enterprise Single Sign-On management user interface to locate and read an XML file that describes the configuration properties for your adapter.</span></span> <span data-ttu-id="67684-106">Les outils de gestion utilisent le fichier XML pour obtenir une page de propriétés réunissant les valeurs de propriété nécessaires, pour l’adaptateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="67684-106">The management tools use the XML file to render a property page to gather the required property values, for the specified adapter.</span></span> <span data-ttu-id="67684-107">Vous pouvez également utiliser ISSOConfigStore pour charger et lire des combinaisons valeur/nom XML depuis et vers le magasin de configuration, ou encore l'outil SSOPS.</span><span class="sxs-lookup"><span data-stu-id="67684-107">You can also use ISSOConfigStore to load and read XML name/value combinations to and from the configuration store, or you can use the SSOPS tool.</span></span>  
  
 <span data-ttu-id="67684-108">Vous pouvez enfin utiliser les outils d’authentification unique de l’entreprise pour activer et désactiver un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="67684-108">You can also use the Enterprise Single Sign-On administration tools to enable and disable an adapter.</span></span> <span data-ttu-id="67684-109">Lors de la création initiale, un adaptateur est désactivé.</span><span class="sxs-lookup"><span data-stu-id="67684-109">On initial creation, an adapter is disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67684-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67684-110">See Also</span></span>  
 [<span data-ttu-id="67684-111">Adaptateurs de synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="67684-111">Password Sync Adapters</span></span>](../core/password-sync-adapters.md)