---
title: Comment configurer un adaptateur de synchronisation de mot de passe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0effdc9b-4aee-4674-90c5-03dfd7cc4cd6
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f0be0146e905ef291942bd30adc111eff89e989
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-password-sync-adapter"></a><span data-ttu-id="c9f69-102">Comment configurer un adaptateur de synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="c9f69-102">How to Configure a Password Sync Adapter</span></span>
<span data-ttu-id="c9f69-103">Après avoir créé votre adaptateur de synchronisation de mot de passe, vous devez le charger sur un système.</span><span class="sxs-lookup"><span data-stu-id="c9f69-103">After you have finished creating your password sync adapter, you must load your adapter on to a system.</span></span> <span data-ttu-id="c9f69-104">En outre, vous devez informer les systèmes d’authentification unique de l’entreprise (ENTSSO) et de stockage des informations de configuration que votre application correspond à un adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="c9f69-104">Additionally, you must inform Enterprise Single Sign-On (ENTSSO) and the configuration store that your application is a password sync adapter.</span></span> <span data-ttu-id="c9f69-105">Vous devez enregistrer le magasin de configuration pour des raisons de sécurité : votre adaptateur demandera de mises à jour les mots de passe et autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="c9f69-105">You must register with the configuration store for security purposes: your adapter will request updates to passwords and other credentials.</span></span> <span data-ttu-id="c9f69-106">Par conséquent, l'authentification unique de l'entreprise (ENTSSO) doit être informée de l’autorisation d'un adaptateur donné à demander de telles autorisations.</span><span class="sxs-lookup"><span data-stu-id="c9f69-106">Therefore, ENTSSO must know that a given adapter is allowed to ask for such permissions.</span></span>  
  
### <a name="to-configure-a-password-sync-adapter"></a><span data-ttu-id="c9f69-107">Pour configurer un adaptateur de synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="c9f69-107">To configure a password sync adapter</span></span>  
  
1.  <span data-ttu-id="c9f69-108">Créez votre adaptateur avec le magasin de configuration à l'aide de l'outil ssops.</span><span class="sxs-lookup"><span data-stu-id="c9f69-108">Create your adapter with the configuration store using the ssops tool.</span></span>  
  
     <span data-ttu-id="c9f69-109">Avec ssops, vous pouvez charger un fichier de configuration XML dans la base de données de configuration qui décrit votre application au système d’authentification unique de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="c9f69-109">Using ssops, you load an XML configuration file into the configuration database that describes your application to Enterprise Single Sign-On.</span></span>  
  
2.  <span data-ttu-id="c9f69-110">Une fois que vous avez créé l’adaptateur avec la base de données de configuration, vous pouvez modifier les informations de l’adaptateur avec `ISSOPSAdmin.SetAdapterProperties`.</span><span class="sxs-lookup"><span data-stu-id="c9f69-110">After you create the adapter with the config database, you can modify the adapter information with `ISSOPSAdmin.SetAdapterProperties`.</span></span>  
  
     <span data-ttu-id="c9f69-111">Les deux méthodes sont semblables, si ce n’est que `SetAdapterProperties` envoie un message à l’adaptateur lorsque les informations de configuration sont modifiées.</span><span class="sxs-lookup"><span data-stu-id="c9f69-111">While the two methods are similar, `SetAdapterProperties` sends a message to the adapter when the configuration information changes.</span></span>  
  
3.  <span data-ttu-id="c9f69-112">Pour supprimer un adaptateur, utilisez ISSOAdmin.DeleteApplication.</span><span class="sxs-lookup"><span data-stu-id="c9f69-112">To delete an adapter, use ISSOAdmin.DeleteApplication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f69-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9f69-113">See Also</span></span>  
 [<span data-ttu-id="c9f69-114">Synchronisation des mots de passe</span><span class="sxs-lookup"><span data-stu-id="c9f69-114">Synchronizing Passwords</span></span>](../core/synchronizing-passwords.md)