---
title: Comment supprimer SSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, deleting
- SSO, deleting
- deleting, SSO
- deleting, Master Secret server
ms.assetid: 0e1ad8e3-0938-4f36-b85b-4631d0eeb8c9
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7134186161c3c0647a20047afcbbe317fcbad1ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-sso"></a><span data-ttu-id="8f38b-102">Comment supprimer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="8f38b-102">How to Remove SSO</span></span>
<span data-ttu-id="8f38b-103">Si vous supprimez BizTalk Server, l'authentification unique de l'entreprise (SSO) n'est ni configurée (sauf si un produit dépendant l'utilise),</span><span class="sxs-lookup"><span data-stu-id="8f38b-103">If you remove BizTalk Server, Enterprise Single Sign-On (SSO) is no longer configured unless a dependent product is using it.</span></span> <span data-ttu-id="8f38b-104">ni supprimée.</span><span class="sxs-lookup"><span data-stu-id="8f38b-104">However, it is not removed.</span></span> <span data-ttu-id="8f38b-105">Vous devez donc supprimer SSO séparément.</span><span class="sxs-lookup"><span data-stu-id="8f38b-105">You must remove SSO separately.</span></span> <span data-ttu-id="8f38b-106">Vous pouvez également restaurer les informations de configuration, y compris le secret principal, afin de réutiliser les données existantes.</span><span class="sxs-lookup"><span data-stu-id="8f38b-106">You can also restore configuration information including the master secret to reuse existing data.</span></span> <span data-ttu-id="8f38b-107">Pour plus d’informations, consultez [comment restaurer le Secret principal](../core/how-to-restore-the-master-secret.md).</span><span class="sxs-lookup"><span data-stu-id="8f38b-107">For more information, see [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md).</span></span>  
  
### <a name="to-remove-enterprise-single-sign-on"></a><span data-ttu-id="8f38b-108">Pour supprimer l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="8f38b-108">To remove Enterprise Single Sign-On</span></span>  
  
1.  <span data-ttu-id="8f38b-109">Sauvegardez la clé du secret principal.</span><span class="sxs-lookup"><span data-stu-id="8f38b-109">Back up the master secret key.</span></span> <span data-ttu-id="8f38b-110">Pour plus d’informations, consultez [comment revenir Up the Master Secret](../core/how-to-back-up-the-master-secret.md).</span><span class="sxs-lookup"><span data-stu-id="8f38b-110">For more information, see [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md).</span></span>  
  
2.  <span data-ttu-id="8f38b-111">Désinstallez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f38b-111">Uninstall [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="8f38b-112">Dans le menu **Démarrer** , cliquez sur **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="8f38b-112">On the **Start** menu, click **Control Panel**.</span></span>  
  
4.  <span data-ttu-id="8f38b-113">Cliquez sur **Ajout/Suppression de programmes**.</span><span class="sxs-lookup"><span data-stu-id="8f38b-113">Click **Add/Remove Programs**.</span></span>  
  
5.  <span data-ttu-id="8f38b-114">Dans le **Ajout/Suppression de programmes** boîte de dialogue, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="8f38b-114">In the **Add/Remove Programs** dialog box, click **Microsoft Enterprise Single Sign-On**, and then click **Remove**.</span></span>  
  
6.  <span data-ttu-id="8f38b-115">Cliquez sur **Oui** lorsque vous êtes invité à confirmer la suppression de Microsoft Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="8f38b-115">Click **Yes** when prompted to confirm the removal of Microsoft Enterprise Single Sign-On.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f38b-116">Si les composants d'exécution, de développement ou d'administration BizTalk Server ou les fonctionnalités d'administration Host Integration Server ne sont pas installés, vous ne pouvez pas désinstaller les composants d'administration ou d'exécution de l'authentification unique tant que toutes les dépendances n'ont pas été désinstallées.</span><span class="sxs-lookup"><span data-stu-id="8f38b-116">If you have BizTalk Server Runtime, Development, or Administration features installed, or Host Integration Server Administration features installed, you will not be able to uninstall the SSO Runtime or Administration components until all dependencies are removed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f38b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f38b-117">See Also</span></span>  
 [<span data-ttu-id="8f38b-118">L’installation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="8f38b-118">Installing SSO</span></span>](../core/installing-sso.md)