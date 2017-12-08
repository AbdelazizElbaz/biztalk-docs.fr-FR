---
title: "AS2 L’utilitaire Sender | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e2a88fc-67fd-4801-a6f8-1e7c92098eaf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e69f70e2a404c92393fb02b301b58abf2d97da2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-sender-utility"></a><span data-ttu-id="b8c64-102">Utilitaire Expéditeur AS2</span><span class="sxs-lookup"><span data-stu-id="b8c64-102">AS2 Sender Utility</span></span>
<span data-ttu-id="b8c64-103">L'utilitaire AS2 Sender inclus avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'envoyer un message AS2 vers un site Web sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b8c64-103">The AS2 Sender utility shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to send an AS2 message to a Web site on a single computer.</span></span> <span data-ttu-id="b8c64-104">Il simule l'envoi d'un message AS2 à partir d'un ordinateur distinct.</span><span class="sxs-lookup"><span data-stu-id="b8c64-104">This utility simulates the sending of an AS2 message from a separate computer.</span></span>  
  
 <span data-ttu-id="b8c64-105">Les fichiers de cet utilitaire sont situés dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender.</span><span class="sxs-lookup"><span data-stu-id="b8c64-105">The AS2 Sender utility files are located in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b8c64-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b8c64-106">Prerequisites</span></span>  
 <span data-ttu-id="b8c64-107">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8c64-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
## <a name="what-this-utility-does"></a><span data-ttu-id="b8c64-108">Fonctions de l'utilitaire</span><span class="sxs-lookup"><span data-stu-id="b8c64-108">What This Utility Does</span></span>  
 <span data-ttu-id="b8c64-109">L'utilitaire AS2 Sender génère un message AS2 avec une charge EDI, puis envoie celui-ci vers un site Web utilisant le filtre ISAPI BTSHTTPReceive.</span><span class="sxs-lookup"><span data-stu-id="b8c64-109">The AS2 Sender utility builds an AS2 message with an EDI payload, and sends that message to a Web site that uses the BTSHTTPReceive ISAPI filter.</span></span> <span data-ttu-id="b8c64-110">Le didacticiel effectue les tâches suivantes par défaut :</span><span class="sxs-lookup"><span data-stu-id="b8c64-110">By default the tutorial does the following:</span></span>  
  
-   <span data-ttu-id="b8c64-111">Envoie un message AS2 nommé X12_00401_864.edi avec une charge 864 X12.</span><span class="sxs-lookup"><span data-stu-id="b8c64-111">Sends an AS2 message named X12_00401_864.edi with an 864 X12-encoded payload.</span></span> <span data-ttu-id="b8c64-112">Ce message se trouve dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial folder.</span><span class="sxs-lookup"><span data-stu-id="b8c64-112">This message is located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial folder.</span></span>  
  
-   <span data-ttu-id="b8c64-113">Demande un MDN asynchrone en réponse au message AS2.</span><span class="sxs-lookup"><span data-stu-id="b8c64-113">Prompts an asynchronous MDN in response to the AS2 message.</span></span> <span data-ttu-id="b8c64-114">Ceci est déterminé par le message envoyé et peut être modifié.</span><span class="sxs-lookup"><span data-stu-id="b8c64-114">This is determined by the message sent, and can be changed.</span></span>  
  
-   <span data-ttu-id="b8c64-115">Envoie le message AS2 vers un emplacement de réception via le répertoire virtuel Contoso.</span><span class="sxs-lookup"><span data-stu-id="b8c64-115">Sends the AS2 message to a receive location through the Contoso virtual directory.</span></span>  
  
 <span data-ttu-id="b8c64-116">L'utilitaire peut être modifié pour changer ce comportement spécifique.</span><span class="sxs-lookup"><span data-stu-id="b8c64-116">The utility can be modified to change this specific behavior.</span></span> <span data-ttu-id="b8c64-117">Consultez le [comment personnaliser l’utilitaire AS2 Sender](../core/as2-sender-utility.md#BKMK_Custom) section ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b8c64-117">See the [How to Customize the AS2 Sender Utility](../core/as2-sender-utility.md#BKMK_Custom) section below.</span></span>  
  
## <a name="how-to-set-up-a-solution-using-the-as2-sender-utility"></a><span data-ttu-id="b8c64-118">Configuration d'une solution se servant de l'utilitaire AS2 Sender</span><span class="sxs-lookup"><span data-stu-id="b8c64-118">How to Set Up a Solution Using the AS2 Sender Utility</span></span>  
 <span data-ttu-id="b8c64-119">Pour configurer une solution pour qu'elle fasse appel à l'utilitaire AS2 Sender, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b8c64-119">To set up a solution to use the AS2 Sender utility, you need to do the following.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8c64-120">Ces étapes sont décrites dans le didacticiel AS2 et dans deux procédures pas à pas AS2 côté envoi.</span><span class="sxs-lookup"><span data-stu-id="b8c64-120">These steps are demonstrated in the AS2 Tutorial and two AS2 send-side walkthroughs.</span></span> <span data-ttu-id="b8c64-121">Pour plus d’informations, consultez [didacticiel 3 : didacticiel AS2](../core/tutorial-3-as2-tutorial.md), [procédure pas à pas (AS2) : envoi d’EDI via AS2 avec un MDN synchrone](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md), et [procédure pas à pas (AS2) : envoi d’EDI via AS2 avec un asynchrone MDN](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md).</span><span class="sxs-lookup"><span data-stu-id="b8c64-121">For more information, see [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md), [Walkthrough (AS2): Sending EDI over AS2 with a Synchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md), and [Walkthrough (AS2): Sending EDI over AS2 with an Asynchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md).</span></span>  
  
-   <span data-ttu-id="b8c64-122">Activez le filtre ISAPI BTSHTTPReceive.</span><span class="sxs-lookup"><span data-stu-id="b8c64-122">Enable the BTSHTTPReceive ISAPI filter.</span></span>  
  
-   <span data-ttu-id="b8c64-123">Configurez une page Web et un emplacement de réception pour recevoir le message AS2.</span><span class="sxs-lookup"><span data-stu-id="b8c64-123">Configure a Web page and a receive location to receive the AS2 message.</span></span> <span data-ttu-id="b8c64-124">Dans l'utilitaire AS2 Sender par défaut, la page Web est la page Web Contoso.</span><span class="sxs-lookup"><span data-stu-id="b8c64-124">In the default AS2 Sender utility, the Web page is the Contoso Web page.</span></span>  
  
-   <span data-ttu-id="b8c64-125">Déployez le schéma de l'échange EDI que vous allez envoyer en tant que charge du message AS2.</span><span class="sxs-lookup"><span data-stu-id="b8c64-125">Deploy the schema for the EDI interchange that you will send as a payload of the AS2 message.</span></span>  
  
-   <span data-ttu-id="b8c64-126">Définissez les propriétés de tiers AS2 et EDI appropriées.</span><span class="sxs-lookup"><span data-stu-id="b8c64-126">Set the appropriate AS2 and EDI party properties.</span></span>  
  
##  <a name="BKMK_Custom"></a><span data-ttu-id="b8c64-127">La personnalisation de l’utilitaire AS2 Sender</span><span class="sxs-lookup"><span data-stu-id="b8c64-127">How to Customize the AS2 Sender Utility</span></span>  
 <span data-ttu-id="b8c64-128">L'utilitaire AS2 Sender par défaut envoie un échange 864 EDI de test via AS2 vers la page Web Contoso à l'aide du filtre ISAPI BTSHTTPReceive.</span><span class="sxs-lookup"><span data-stu-id="b8c64-128">The default AS2 Sender utility sends a test 864 EDI interchange over AS2 to a Contoso Web page using the BTSHTTPReceive ISAPI filter.</span></span> <span data-ttu-id="b8c64-129">Le message AS2, nommé X12_00401_864.edi, demande un MDN asynchrone.</span><span class="sxs-lookup"><span data-stu-id="b8c64-129">The AS2 message, named X12_00401_864.edi, prompts an asynchronous MDN.</span></span> <span data-ttu-id="b8c64-130">Le code de l'utilitaire AS2 Sender est situé dans HttpSender.cs dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]AS2 Tutorial\Sender.</span><span class="sxs-lookup"><span data-stu-id="b8c64-130">The AS2 Sender utility code is located in HttpSender.cs in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]AS2 Tutorial\Sender folder.</span></span> <span data-ttu-id="b8c64-131">La ligne de code suivante dans HttpSender.cs envoie le fichier de test 864 par défaut :</span><span class="sxs-lookup"><span data-stu-id="b8c64-131">The following line of code in HttpSender.cs sends the default 864 test file:</span></span>  
  
```  
Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864.edi", FileMode.Open, FileAccess.Read);  
```  
  
> [!NOTE]
>  <span data-ttu-id="b8c64-132">Vous pouvez modifier cette ligne en changeant le nom et le chemin d'accès du fichier.</span><span class="sxs-lookup"><span data-stu-id="b8c64-132">You can modify this line with a different file name and different path.</span></span>  
  
 <span data-ttu-id="b8c64-133">La ligne suivante dans HttpSender.cs envoie un message AS2 nommé X12_00401_864-Sync.EDI.</span><span class="sxs-lookup"><span data-stu-id="b8c64-133">The following line in HttpSender.cs sends an AS2 message named X12_00401_864-Sync.edi.</span></span> <span data-ttu-id="b8c64-134">Ce message demande un MDN synchrone.</span><span class="sxs-lookup"><span data-stu-id="b8c64-134">This message prompts a synchronous MDN.</span></span> <span data-ttu-id="b8c64-135">Par défaut, cette ligne de code dans HttpSender.cs est commentée en faveur de la ligne qui envoie X12_00401_864.edi.</span><span class="sxs-lookup"><span data-stu-id="b8c64-135">By default, this line of code in HttpSender.cs is commented out in favor of the line that sends X12_00401_864.edi.</span></span> <span data-ttu-id="b8c64-136">Pour envoyer X12_00401_864-Sync.edi, supprimez le commentaire de la ligne X12_00401_864-Sync.edi et commentez la ligne X12_00401_864.edi.</span><span class="sxs-lookup"><span data-stu-id="b8c64-136">To send X12_00401_864-Sync.edi, uncomment the X12_00401_864-Sync.edi line and comment out the X12_00401_864.edi line.</span></span>  
  
```  
Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864-Sync.edi", FileMode.Open, FileAccess.Read);  
```  
  
 <span data-ttu-id="b8c64-137">La ligne de code suivante dans HttpSender.cs envoie le message vers la page Web Contoso :</span><span class="sxs-lookup"><span data-stu-id="b8c64-137">The following line of code in HttpSender.cs sends the message to the Contoso Web page:</span></span>  
  
```  
HttpSender TestSender = new HttpSender("http://localhost/Contoso/BTSHttpReceive.dll");  
```  
  
> [!NOTE]
>  <span data-ttu-id="b8c64-138">Vous pouvez modifier cette ligne en changeant le répertoire virtuel et le filtre ISAPI.</span><span class="sxs-lookup"><span data-stu-id="b8c64-138">You can modify this line with a different virtual directory and ISAPI filter.</span></span>  
  
### <a name="to-build-the-as2-sender-sample"></a><span data-ttu-id="b8c64-139">Pour créer l'exemple AS2 Sender</span><span class="sxs-lookup"><span data-stu-id="b8c64-139">To build the AS2 Sender sample</span></span>  
  
1.  <span data-ttu-id="b8c64-140">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le projet Sender.csproj dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender.</span><span class="sxs-lookup"><span data-stu-id="b8c64-140">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the Sender.csproj project in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender folder.</span></span>  
  
2.  <span data-ttu-id="b8c64-141">Ouvrez HttpSender.cs dans le projet Sender, puis personnalisez le code Sender en indiquant la page Web de réception, le nom de fichier EDI et le chemin d'accès appropriés.</span><span class="sxs-lookup"><span data-stu-id="b8c64-141">Open HttpSender.cs in the Sender project, and customize the Sender code with the appropriate receiving Web page and the appropriate EDI filename and path.</span></span>  
  
3.  <span data-ttu-id="b8c64-142">Cliquez sur le projet Sender, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b8c64-142">Right-click the Sender project, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b8c64-143">Cliquez sur **signature** dans la console de gauche.</span><span class="sxs-lookup"><span data-stu-id="b8c64-143">Click **Signing** in the left-hand console.</span></span> <span data-ttu-id="b8c64-144">Vérifiez que **signer l’assembly** est sélectionnée, et le fichier de clé de nom fort est défini sur **Sender.snk**.</span><span class="sxs-lookup"><span data-stu-id="b8c64-144">Ensure that **Sign the assembly** is selected, and the strong name key file is set to **Sender.snk**.</span></span> <span data-ttu-id="b8c64-145">Assurez-vous que **temporiser la signature uniquement** est désactivée.</span><span class="sxs-lookup"><span data-stu-id="b8c64-145">Make sure that **Delay sign only** is cleared.</span></span>  
  
5.  <span data-ttu-id="b8c64-146">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="b8c64-146">Build the project.</span></span>  
  
### <a name="to-run-the-as2-sender-sample"></a><span data-ttu-id="b8c64-147">Pour exécuter l'exemple AS2 Sender</span><span class="sxs-lookup"><span data-stu-id="b8c64-147">To run the AS2 Sender sample</span></span>  
  
1.  <span data-ttu-id="b8c64-148">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="b8c64-148">Open a command prompt.</span></span> <span data-ttu-id="b8c64-149">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="b8c64-149">Move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug.</span></span>  
  
2.  <span data-ttu-id="b8c64-150">Entrée **Sender.exe**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="b8c64-150">Enter **Sender.exe**, and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="b8c64-151">Si un message indique que le message AS2 a été correctement envoyé, vous pouvez fermer l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="b8c64-151">Verify that you see a message indicating that an AS2 message was successfully sent, and then close the command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c64-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8c64-152">See Also</span></span>  
 <span data-ttu-id="b8c64-153">[Didacticiel 3 : Didacticiel AS2](../core/tutorial-3-as2-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="b8c64-153">[Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md) </span></span>  
 <span data-ttu-id="b8c64-154">[Procédure pas à pas (AS2) : Envoi d’EDI via AS2 avec un MDN synchrone](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md) </span><span class="sxs-lookup"><span data-stu-id="b8c64-154">[Walkthrough (AS2): Sending EDI over AS2 with a Synchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md) </span></span>  
 [<span data-ttu-id="b8c64-155">Procédure pas à pas (AS2) : Envoi d’EDI via AS2 avec MDN asynchrone</span><span class="sxs-lookup"><span data-stu-id="b8c64-155">Walkthrough (AS2): Sending EDI over AS2 with an Asynchronous MDN</span></span>](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md)