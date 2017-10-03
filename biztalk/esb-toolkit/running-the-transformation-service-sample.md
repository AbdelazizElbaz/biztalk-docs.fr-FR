---
title: "Exécution de l’exemple de Service de Transformation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42064d32-5ec5-4219-a338-c5769969b958
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ac733f3164a319ed0b86e0f609de8ccd03bdbca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-transformation-service-sample"></a><span data-ttu-id="a17f0-102">Exécution de l’exemple de Service de Transformation</span><span class="sxs-lookup"><span data-stu-id="a17f0-102">Running the Transformation Service Sample</span></span>
<span data-ttu-id="a17f0-103">Vous pouvez exécuter l’exemple de Service de Transformation à l’aide de n’importe quel outil ou un utilitaire qui peut exécuter des méthodes de service Web.</span><span class="sxs-lookup"><span data-stu-id="a17f0-103">You can execute the Transformation Service sample using any tool or utility that can execute Web service methods.</span></span> <span data-ttu-id="a17f0-104">Par exemple, vous pouvez utiliser Storm, disponible à partir de [CodePlex](http://go.microsoft.com/fwlink/?LinkId=187762) ([http://go.microsoft.com/fwlink/?LinkId=187762](http://go.microsoft.com/fwlink/?LinkId=187762)), ou vous pouvez créer votre propre client de test qui appelle le service Web de la Transformation.</span><span class="sxs-lookup"><span data-stu-id="a17f0-104">For example, you can use Storm, available from [CodePlex](http://go.microsoft.com/fwlink/?LinkId=187762) ([http://go.microsoft.com/fwlink/?LinkId=187762](http://go.microsoft.com/fwlink/?LinkId=187762)), or you can create your own test client that invokes the Transformation Web service.</span></span>  
  
 <span data-ttu-id="a17f0-105">Pour utiliser le Studio de Service Web .NET pour tester l’installation correcte de l’exemple de Service de Transformation, entrez l’URL du service Web de Transformation basés sur ASMX dans le **point de terminaison WSDL** zone de texte, puis cliquez sur le  **Obtenir** bouton.</span><span class="sxs-lookup"><span data-stu-id="a17f0-105">To use the .NET Web Service Studio to test for correct installation of the Transformation Service sample, enter the URL for the ASMX-based Transformation Web service into the **WSDL EndPoint** text box, and then click the **Get** button.</span></span> <span data-ttu-id="a17f0-106">Cela génère une interface frontale client que vous pouvez utiliser pour appeler le Service Web de Transformation ESB, comme indiqué dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="a17f0-106">This generates a client front-end interface that you can use to call the ESB Transformation Web Service, as shown in Figure 1.</span></span>  
  
 <span data-ttu-id="a17f0-107">![Service de transformation](../esb-toolkit/media/ch6-transformationservice.gif "§ 6-TransformationService")</span><span class="sxs-lookup"><span data-stu-id="a17f0-107">![Transformation Service](../esb-toolkit/media/ch6-transformationservice.gif "Ch6-TransformationService")</span></span>  
  
 <span data-ttu-id="a17f0-108">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="a17f0-108">**Figure 1**</span></span>  
  
 <span data-ttu-id="a17f0-109">**À l’aide du Studio de Service Web .NET pour tester l’exemple de Service de Transformation**</span><span class="sxs-lookup"><span data-stu-id="a17f0-109">**Using the .NET Web Service Studio to test the Transformation Service sample**</span></span>  
  
 <span data-ttu-id="a17f0-110">L’exemple de Service de Transformation contienne deux mappages Microsoft BizTalk et deux documents de message XML de test.</span><span class="sxs-lookup"><span data-stu-id="a17f0-110">The Transformation Service sample contains two Microsoft BizTalk maps and two test XML message documents.</span></span> <span data-ttu-id="a17f0-111">Vous pouvez exécuter le service Web de Transformation avec les messages XML nommés TEST_CanonicalOrder_to_OrderConfirmation.xml et TEST_RetailOrder_to_CanonicalOrder.xml (situé dans le dossier \Source\Samples\TransformServices\Test\Data).</span><span class="sxs-lookup"><span data-stu-id="a17f0-111">You can execute the Transformation Web service with the XML messages named TEST_CanonicalOrder_to_OrderConfirmation.xml and TEST_RetailOrder_to_CanonicalOrder.xml (located in the \Source\Samples\TransformServices\Test\Data folder).</span></span>  
  
 <span data-ttu-id="a17f0-112">Le service transforme automatiquement les messages à l’aide de schémas CanonicalOrder.xsd et RetailOrder.xsd et OrderConfirmation.xsd (situé dans le \Source\Samples\TransformServices\Source\ESB. Dossier TransformServices.Schemas), et .NET Web Service Studio affiche les messages transformées résultantes.</span><span class="sxs-lookup"><span data-stu-id="a17f0-112">The service will automatically transform the messages using the schemas CanonicalOrder.xsd and RetailOrder.xsd and OrderConfirmation.xsd (located in the \Source\Samples\TransformServices\Source\ESB.TransformServices.Schemas folder), and .NET Web Service Studio will display the resulting transformed messages.</span></span> <span data-ttu-id="a17f0-113">La procédure suivante montre comment vous pouvez tester le mappage de CanonicalOrder_To_OrderConfirmation.</span><span class="sxs-lookup"><span data-stu-id="a17f0-113">The following procedure shows how you can test the CanonicalOrder_To_OrderConfirmation map.</span></span>  
  
 <span data-ttu-id="a17f0-114">**Pour tester le mappage GlobalBank.ESB.TransformServices.Maps.CanonicalOrder_To_OrderConfirmation**</span><span class="sxs-lookup"><span data-stu-id="a17f0-114">**To test the GlobalBank.ESB.TransformServices.Maps.CanonicalOrder_To_OrderConfirmation map**</span></span>  
  
1.  <span data-ttu-id="a17f0-115">Si l’application GlobalBank.ESB n’est pas en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.</span><span class="sxs-lookup"><span data-stu-id="a17f0-115">If the GlobalBank.ESB application is not running, use the BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="a17f0-116">Entrez la représentation sous forme de chaîne suivantes du fichier TEST_CanonicalOrder_to_OrderConfirmation.xml en tant que la valeur de la **message** paramètre dans le **entrée** arborescence de Studio de Service Web .NET.</span><span class="sxs-lookup"><span data-stu-id="a17f0-116">Enter the following string representation of the TEST_CanonicalOrder_to_OrderConfirmation.xml file as the value of the **message** parameter in the **Input** tree view of .NET Web Service Studio.</span></span> <span data-ttu-id="a17f0-117">Cette chaîne est conforme au schéma GlobalBank.ESB.TransformServices.Schemas.CanonicalOrder :</span><span class="sxs-lookup"><span data-stu-id="a17f0-117">This string conforms to the GlobalBank.ESB.TransformServices.Schemas.CanonicalOrder schema:</span></span>  
  
    ```  
    <ns0:CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1"   
        Status="Status_2" xmlns:ns0=  
        "http://schemas.globalbank.esb.transformservices.com">  
        <OrderHeader><CustomerName>CustomerName_0</CustomerName>  
        <CustomerID>CustomerID_0</CustomerID><ShipToLine1>  
        ShipToLine1_0</ShipToLine1><ShipToLine2>ShipToLine2_0  
        </ShipToLine2><BillToLine1>BillToLine1_0</BillToLine1>  
        <BillToLine2>BillToLine2_0</BillToLine2><OrderTotal>OrderTotal_0  
        </OrderTotal></OrderHeader><OrderDetails><LineItem Qty="Qty_0"   
        PartNum="PartNum_1" Description="Description_2"   
        UnitPrice="UnitPrice_3" Ext="Ext_4" /></OrderDetails>  
        <B2BPartnerDetails CreditLimit="CreditLimit_0"   
        AccountBalance="AccountBalance_1"   
        LastOrderedData="LastOrderedData_2"   
        DiscountLevel="DiscountLevel_3" /></ns0:CanonicalOrder>  
    ```  
  
3.  <span data-ttu-id="a17f0-118">Entrez la chaîne suivante en tant que la valeur de la **mapName** paramètre dans le **entrée** arborescence de Studio de Service Web .NET.</span><span class="sxs-lookup"><span data-stu-id="a17f0-118">Enter the following string as the value of the **mapName** parameter in the **Input** tree view of .NET Web Service Studio.</span></span> <span data-ttu-id="a17f0-119">Il s’agit du nom complet tapé du mappage BizTalk à exécuter sur le message :</span><span class="sxs-lookup"><span data-stu-id="a17f0-119">This is the fully typed name of the BizTalk map to execute against the message:</span></span>  
  
    ```  
    GlobalBank.ESB.TransformServices.Maps.CanonicalOrder_To_  
        OrderConfirmation, GlobalBank.ESB.TransformServices.Maps,   
        Version=1.0.0.0, Culture=neutral, PublicKeyToken=<insertYourPublicKeyTokenHere>  
    ```  
  
4.  <span data-ttu-id="a17f0-120">Cliquez sur le **Invoke** bouton pour exécuter le service Web.</span><span class="sxs-lookup"><span data-stu-id="a17f0-120">Click the **Invoke** button to execute the Web service.</span></span> <span data-ttu-id="a17f0-121">Le **sortie** test affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="a17f0-121">The **Output** test box displays the results.</span></span>