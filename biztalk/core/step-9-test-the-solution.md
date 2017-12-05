---
title: "Étape 9 : Tester la Solution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df446ccc-add3-4dd3-b674-253dda385541
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89a3722d6d8e1d4b730341dfaf16d60af1686f21
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-9-test-the-solution"></a><span data-ttu-id="e6e2b-102">Étape 9 : Tester la Solution</span><span class="sxs-lookup"><span data-stu-id="e6e2b-102">Step 9: Test the Solution</span></span>
<span data-ttu-id="e6e2b-103">Cette rubrique vous invite à tester l’application hybride via l’envoi d’un message de commande client X12 840 vers le point de terminaison HTTP où est déployé l’accord EDI.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-103">In this topic you test the hybrid application by sending a X12 840 sales order message to the HTTP endpoint where the EDI agreement is deployed.</span></span> <span data-ttu-id="e6e2b-104">L’exemple de message de commande client ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="e6e2b-104">The sample sales order message looks like the following:</span></span>  
  
```  
ISA*00*          *00*          *ZZ*CONTOSO        *ZZ*NORTHWIND      *991221*1226*U*00401*000000025*0*T*:~  
GS*PO*THEM*US*19991221*1226*1*X*004010~  
ST*840*0002~  
BQT*00*BQT02*20120619*001*20120719~  
PER*1A*John*EM*John@contoso.com~  
N1*001~  
N2*co~  
N3*Contoso*One Contoso Way~  
N4*Redmond*WA*98052*US~  
PO1*PO101*121*01*10*AA*A1*1~  
CTT*475~  
SE*10*0002~  
GE*1*1~  
IEA*1*000000025~  
```  
  
 <span data-ttu-id="e6e2b-105">Dans ce message, le segment en surbrillance (ligne commençant par **PO1**) contient la quantité commandée.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-105">In this message, the highlighted segment (the line starting with **PO1**) contains the order quantity.</span></span> <span data-ttu-id="e6e2b-106">La quantité commandée dans ce message est *121*.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-106">The order quantity in this message is *121*.</span></span> <span data-ttu-id="e6e2b-107">Par conséquent, si vous envoyez ce message, il doit être inséré dans le **SalesOrder** table.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-107">So, if you send this message, it must be inserted into the **SalesOrder** table.</span></span> <span data-ttu-id="e6e2b-108">Vous pouvez définir la quantité sur une valeur inférieure à 100 et renvoyer le message. Celui-ci doit ensuite être envoyé à l’emplacement de fichier que vous avez spécifié dans le port d’envoi FILE.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-108">You can update the quantity to less than 100 and resend the message, it must then be sent to the file location you specified in the FILE send port.</span></span>  
  
 <span data-ttu-id="e6e2b-109">Pour envoyer ce message à l’accord EDI, vous pouvez utiliser la **MessageSender** outil fourni avec les exemples de [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e6e2b-109">To send this message to the EDI agreement, you can use the **MessageSender** tool shipped with the samples for [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)].</span></span> <span data-ttu-id="e6e2b-110">Vous pouvez télécharger les exemples à partir de [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057).</span><span class="sxs-lookup"><span data-stu-id="e6e2b-110">You can download the samples from [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057).</span></span>  
  
### <a name="to-send-a-message"></a><span data-ttu-id="e6e2b-111">Pour envoyer un message</span><span class="sxs-lookup"><span data-stu-id="e6e2b-111">To send a message</span></span>  
  
1.  <span data-ttu-id="e6e2b-112">Recherchez le **MessageSender** dans l’exemple de package de projet et générez-le.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-112">Locate the **MessageSender** project in the sample package and build it.</span></span>  
  
2.  <span data-ttu-id="e6e2b-113">Utilisez résultant **MessageSender** exécutable de ligne de commande (sous le dossier \bin\Debug du projet) pour envoyer des messages à l’accord EDI déployé.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-113">Use the resulting **MessageSender** command-line executable (under \bin\Debug folder within the project) to send messages to the deployed EDI agreement.</span></span> <span data-ttu-id="e6e2b-114">Cet outil accepte le paramètre de ligne de commande au format suivant :</span><span class="sxs-lookup"><span data-stu-id="e6e2b-114">This tool accepts command-line parameter in the following format:</span></span>  
  
    ```  
    MessageSender.exe <ServiceBusNamespace> <IssuerName> <IssuerKey> <EDI agreement endpoint> <MessageFilepath> <ContentType>  
    ```  
  
     <span data-ttu-id="e6e2b-115">WHERE,</span><span class="sxs-lookup"><span data-stu-id="e6e2b-115">Where,</span></span>  
  
    |<span data-ttu-id="e6e2b-116">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="e6e2b-116">Parameter name</span></span>|<span data-ttu-id="e6e2b-117"> Description</span><span class="sxs-lookup"><span data-stu-id="e6e2b-117">Description</span></span>|  
    |--------------------|-----------------|  
    |<span data-ttu-id="e6e2b-118">ServiceBusNamespace</span><span class="sxs-lookup"><span data-stu-id="e6e2b-118">ServiceBusNamespace</span></span>|<span data-ttu-id="e6e2b-119">Espace de noms du Service Bus</span><span class="sxs-lookup"><span data-stu-id="e6e2b-119">The Service Bus namespace</span></span>|  
    |<span data-ttu-id="e6e2b-120">IssuerName</span><span class="sxs-lookup"><span data-stu-id="e6e2b-120">IssuerName</span></span>|<span data-ttu-id="e6e2b-121">Nom de l’émetteur pour l’espace de noms spécifié</span><span class="sxs-lookup"><span data-stu-id="e6e2b-121">Issuer Name for the specified namespace</span></span>|  
    |<span data-ttu-id="e6e2b-122">IssuerKey</span><span class="sxs-lookup"><span data-stu-id="e6e2b-122">IssuerKey</span></span>|<span data-ttu-id="e6e2b-123">Clé de l’émetteur pour l’espace de noms spécifié</span><span class="sxs-lookup"><span data-stu-id="e6e2b-123">Issuer Key for the specified namespace</span></span>|  
    |<span data-ttu-id="e6e2b-124">Point de terminaison de l’accord EDI</span><span class="sxs-lookup"><span data-stu-id="e6e2b-124">EDI agreement endpoint</span></span>|<span data-ttu-id="e6e2b-125">Point de terminaison où est déployé l’accord EDI.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-125">The endpoint where the EDI agreement is deployed.</span></span> <span data-ttu-id="e6e2b-126">Vous pouvez obtenir cette URL de point de terminaison à partir de l’onglet Paramètres de réception (et dans laquelle la page Transport) de l’accord EDI que vous avez déployé dans [étape 2 (pour Azure) : création d’un accord EDI](../core/step-2-for-azure-create-an-edi-agreement.md).</span><span class="sxs-lookup"><span data-stu-id="e6e2b-126">You can get this endpoint URL from the Receive Settings tab (and within that, the Transport page) of the EDI agreement you deployed in [Step 2 (For Azure): Create an EDI Agreement](../core/step-2-for-azure-create-an-edi-agreement.md).</span></span>|  
    |<span data-ttu-id="e6e2b-127">MessageFilePath</span><span class="sxs-lookup"><span data-stu-id="e6e2b-127">MessageFilePath</span></span>|<span data-ttu-id="e6e2b-128">Chemin d’accès au fichier contenant l’exemple de message de requête.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-128">Path to the file that contains the sample request message.</span></span>|  
    |<span data-ttu-id="e6e2b-129">ContentType</span><span class="sxs-lookup"><span data-stu-id="e6e2b-129">ContentType</span></span>|<span data-ttu-id="e6e2b-130">Pour ce didacticiel, définissez ce paramètre sur **texte/brut**.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-130">For this tutorial, set this parameter to **text/plain**.</span></span>|  
  
     <span data-ttu-id="e6e2b-131">Ouvrez une invite de commandes et accédez à la solution dans laquelle vous avez créé le **MessageSender** projet.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-131">Open a command prompt and navigate to the solution where you built the **MessageSender** project.</span></span> <span data-ttu-id="e6e2b-132">Exécutez la commande suivante pour envoyer le message de requête avec une quantité commandée inférieure à 100 :</span><span class="sxs-lookup"><span data-stu-id="e6e2b-132">Run the following command to send the request message with order quantity more than 100:</span></span>  
  
    ```  
    MessageSender.exe <service bus namespace> owner <issuer key>https://<namespace>.servicebus.appfabriclabs.com/7576ff3d-a0f3-4a46-a4f6-f5be4a50616a/DemoAgreement<path to the sample message> "text/plain"  
    ```  
  
3.  <span data-ttu-id="e6e2b-133">Ouvrez SQL Server Management Studio, connectez-vous à la base de données qui contient le **SalesOrder** de table et vérifiez qu’un nouvel enregistrement est inséré dans la table.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-133">Open SQL Server Management Studio, connect to the database that contains the **SalesOrder** table, and verify that a new record is inserted into the table.</span></span> <span data-ttu-id="e6e2b-134">Notez la valeur dans la **Qty** colonne ; il doit être *121*.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-134">Notice the value in the **Qty** column; it must be *121*.</span></span>  
  
4.  <span data-ttu-id="e6e2b-135">Utilisez **MessageSender** pour envoyer un autre message, mais cette fois la valeur de la quantité commandée dans le message à *99*.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-135">Use **MessageSender** to send another message, but this time set the value of the quantity ordered in the message to *99*.</span></span> <span data-ttu-id="e6e2b-136">Vous remarquerez qu’à présent aucun enregistrement n’est inséré dans le **SalesOrder** table.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-136">You will notice that now, no record is inserted in the **SalesOrder** table.</span></span> <span data-ttu-id="e6e2b-137">Au lieu de cela, le message est copié vers l’emplacement de fichier spécifié pour la réception des messages par quantité commandée inférieure à 100.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-137">Instead, the message is copied to the file location you specified for receiving messages with order quantity less than 100.</span></span> <span data-ttu-id="e6e2b-138">Le message reçu ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="e6e2b-138">The received message resembles the following:</span></span>  
  
    ```  
    <ns1:SalesOrder xmlns:ns0="http://schemas.microsoft.com/BizTalk/EDI/X12/2006" xmlns:ns1="http://ECommerceSalesOrder.Inbound">  
      <CompanyCode>co</CompanyCode>  
      <PartID>1</PartID>  
      <Quantity>99</Quantity>  
      <AskPrice>10</AskPrice>  
      <RequestShipmentDate>2012-07-19</RequestShipmentDate>  
      <Address>  
        <Line1>Contoso</Line1>  
        <Line2>One Contoso Way</Line2>  
        <City>Redmond</City>  
        <State>WA</State>  
        <Country>US</Country>  
        <Zipcode>98052</Zipcode>  
      </Address>  
      <Contact>  
        <Firstname>John</Firstname>  
        <Lastname>John@contoso.com</Lastname>  
      </Contact>  
      <Comments>Order from Partnerco</Comments>  
      <DateNow>2012-06-19</DateNow>  
    </ns1:SalesOrder>  
  
    ```  
  
     <span data-ttu-id="e6e2b-139">Notez la valeur dans la **quantité** élément.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-139">Notice the value in the **Quantity** element.</span></span> <span data-ttu-id="e6e2b-140">Il s’agit de *99*.</span><span class="sxs-lookup"><span data-stu-id="e6e2b-140">It is *99*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e2b-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6e2b-141">See Also</span></span>  
 [<span data-ttu-id="e6e2b-142">Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="e6e2b-142">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)