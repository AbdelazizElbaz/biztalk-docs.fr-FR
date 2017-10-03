---
title: Comment restaurer le magasin de certificats | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c6f7551-d119-4668-9b52-6013f69a0302
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aaeee6b762cf5af15ca7cba34864abd86682d4df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-restore-the-certificate-store"></a><span data-ttu-id="f2c41-102">Restauration du magasin de certificats</span><span class="sxs-lookup"><span data-stu-id="f2c41-102">How to Restore the Certificate Store</span></span>
<span data-ttu-id="f2c41-103">Dans le cadre de la récupération de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez restaurer le magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="f2c41-103">As a part of recovering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you must restore the certificate store.</span></span> <span data-ttu-id="f2c41-104">Si vous récupérez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Édition Standard, vous devez utiliser cette procédure pour restaurer le magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="f2c41-104">If you are recovering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition, you must use this procedure to restore the certificate store.</span></span> <span data-ttu-id="f2c41-105">Vous ne devez pas utiliser cette procédure pour récupérer d'autres éditions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] car le processus de récupération restaure automatiquement le magasin de certificats pour vous.</span><span class="sxs-lookup"><span data-stu-id="f2c41-105">You do not need to perform this procedure when recovering all other editions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] because the recovery process automatically restores the certificate store for you.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f2c41-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f2c41-106">Prerequisites</span></span>  
 <span data-ttu-id="f2c41-107">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="f2c41-107">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
### <a name="to-restore-the-certificate-store-biztalk-server-standard-edition"></a><span data-ttu-id="f2c41-108">Pour restaurer le magasin de certificats (BizTalk Server Édition Standard)</span><span class="sxs-lookup"><span data-stu-id="f2c41-108">To restore the certificate store (BizTalk Server Standard Edition)</span></span>  
  
1.  <span data-ttu-id="f2c41-109">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, puis cliquez sur **Internet Explorer**.</span><span class="sxs-lookup"><span data-stu-id="f2c41-109">Click **Start**, click **All Programs**, and then click **Internet Explorer**.</span></span>  
  
2.  <span data-ttu-id="f2c41-110">Sur le **outils** menu, cliquez sur **Options Internet**.</span><span class="sxs-lookup"><span data-stu-id="f2c41-110">On the **Tools** menu, click **Internet Options**.</span></span>  
  
3.  <span data-ttu-id="f2c41-111">Dans le **Options Internet** boîte de dialogue, cliquez sur le **contenu** onglet, puis cliquez sur **certificats**.</span><span class="sxs-lookup"><span data-stu-id="f2c41-111">In the **Internet Options** dialog box, click the **Content** tab, and then click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="f2c41-112">Dans le **certificats** boîte de dialogue, cliquez sur le **autres personnes** onglet, puis cliquez sur **importation**.</span><span class="sxs-lookup"><span data-stu-id="f2c41-112">In the **Certificates** dialog box, click the **Other People** tab, and then click **Import**.</span></span>  
  
5.  <span data-ttu-id="f2c41-113">Dans le **Assistant Importation de certificat**, cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="f2c41-113">In the **Certificate Import Wizard**, click **Cancel**.</span></span>  
  
     <span data-ttu-id="f2c41-114">Cette opération crée le **carnet d’adresses** ruche dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="f2c41-114">This creates the **AddressBook** hive in the registry.</span></span>  
  
6.  <span data-ttu-id="f2c41-115">Dans le **certificats** boîte de dialogue, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="f2c41-115">In the **Certificates** dialog box, click **Close**.</span></span>  
  
7.  <span data-ttu-id="f2c41-116">Dans le **Options Internet** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f2c41-116">In the **Internet Options** dialog box, click **OK**.</span></span>  
  
8.  <span data-ttu-id="f2c41-117">Cliquez sur **fichier**, puis cliquez sur **fermer** quitter Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f2c41-117">Click **File**, and then click **Close** to exit Internet Explorer.</span></span>  
  
9. <span data-ttu-id="f2c41-118">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **regedit**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f2c41-118">Click **Start**, click **Run**, type **regedit**, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="f2c41-119">Dans l'Éditeur du Registre, accédez à la clé de Registre suivante :</span><span class="sxs-lookup"><span data-stu-id="f2c41-119">In Registry Editor, navigate to the following registry key:</span></span>  
  
     <span data-ttu-id="f2c41-120">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates**</span><span class="sxs-lookup"><span data-stu-id="f2c41-120">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates**</span></span>  
  
11. <span data-ttu-id="f2c41-121">Vérifiez que le **carnet d’adresses** ruche est présent.</span><span class="sxs-lookup"><span data-stu-id="f2c41-121">Verify that the **AddressBook** hive is present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2c41-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2c41-122">See Also</span></span>  
 [<span data-ttu-id="f2c41-123">Récupération d’un ordinateur exécutant BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f2c41-123">Recovering a Computer Running BizTalk Server</span></span>](../core/recovering-a-computer-running-biztalk-server.md)