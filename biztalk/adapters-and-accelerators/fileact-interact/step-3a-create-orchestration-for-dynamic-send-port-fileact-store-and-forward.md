---
title: "Étape 3 a : création d’une orchestration pour le port d’envoi dynamique pour le scénario (Pull) avant d’et de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5675d476-ad36-4bbc-8e87-786edc9c805d
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c91f9054885de1d19b467646ee7b82b342a76d6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-create-an-orchestration-for-dynamic-send-port-for-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="f8eb3-102">Étape 3 a : création d’une orchestration pour le port d’envoi dynamique pour le scénario (Pull) avant d’et de FileAct</span><span class="sxs-lookup"><span data-stu-id="f8eb3-102">Step 3A: Create an orchestration for dynamic send port for FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="f8eb3-103">Avant de commencer les étapes décrites dans cette section, vous devez effectuer les étapes décrites dans le [étape 2c : ajouter un Port d’envoi FILEACT pour et le scénario de (extraits) avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-2c-add-a-fileact-send-port-for-fileact-store-and-forward-pull-scenario.md) section.</span><span class="sxs-lookup"><span data-stu-id="f8eb3-103">Before you begin the steps in this section, you must complete the steps in the [Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2c-add-a-fileact-send-port-for-fileact-store-and-forward-pull-scenario.md) section.</span></span>  
  
### <a name="to-create-an-orchestration"></a><span data-ttu-id="f8eb3-104">Pour créer une Orchestration</span><span class="sxs-lookup"><span data-stu-id="f8eb3-104">To Create an Orchestration</span></span>  
  
1.  <span data-ttu-id="f8eb3-105">Créez la forme réception qui s’abonne à tous les messages du type de message Sw-ExchangeSnFRequest.</span><span class="sxs-lookup"><span data-stu-id="f8eb3-105">Create the Receive shape that subscribes to all of the messages of message type Sw-ExchangeSnFRequest.</span></span>  
  
2.  <span data-ttu-id="f8eb3-106">Ajoutez une forme Expression pour obtenir toutes les valeurs requises à partir du message ExchangeRequestSnF.</span><span class="sxs-lookup"><span data-stu-id="f8eb3-106">Add an Expression shape to get all of the required values from the ExchangeRequestSnF message.</span></span> <span data-ttu-id="f8eb3-107">Reportez-vous à l’exemple suivant de la forme Expression :</span><span class="sxs-lookup"><span data-stu-id="f8eb3-107">Refer to the following Expression Shape sample:</span></span>  
  
    ```  
    ExchangeSnFRequestDoc=ExchangeSnFRequest;  
    AcquireQueuePath="/Sw-ExchangeSnFRequest/Sw-SnFRequest/Sw-SnFOpRequest/Sw-AcquireSnFRequest/";  
  
    QueueNameNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath + "SwInt-Queue");  
    SessionModeNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-SessionMode");  
    ForceAcquireNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-ForceAcquire");  
    OrderByNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-OrderBy");  
    RecoveryModeNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-RecoveryMode");  
  
    QueueName=QueueNameNode.InnerText;  
    SessionMode=SessionModeNode.InnerText;  
    ForceAcquire=ForceAcquireNode.InnerText;  
    OrderBy=OrderByNode.InnerText;  
    RecoveryMode=RecoveryModeNode.InnerText;  
  
    MessageFormat="FileactMessage";  
    IsPull=true;  
  
    ```  
  
3.  <span data-ttu-id="f8eb3-108">Construire un message de type PullSnFRequest et l’URL pour l’envoi dynamique.</span><span class="sxs-lookup"><span data-stu-id="f8eb3-108">Construct a message of type PullSnFRequest and the URL for Dynamic Send.</span></span> <span data-ttu-id="f8eb3-109">Consultez l’exemple d’attribution forme de construire un Message :</span><span class="sxs-lookup"><span data-stu-id="f8eb3-109">Refer to the Assignment Shape of Construct Message sample:</span></span>  
  
    ```  
    PullMessage = new System.Xml.XmlDocument();  
    PullMessage.LoadXml(@"<Sw-PullSnFRequest/>");  
    PullRequest = PullMessage;  
  
    DynamicPull(Microsoft.XLANGs.BaseTypes.Address) = "FILEACT://localhost/" + QueueName + "/" + SessionMode + "/" + ForceAcquire + "/" + OrderBy + "/" + RecoveryMode + "/" + MessageFormat;  
  
    ```  
  
4.  <span data-ttu-id="f8eb3-110">Dans cet exemple, PullMessage est un message de type Sw-PullSnFRequest.</span><span class="sxs-lookup"><span data-stu-id="f8eb3-110">In this sample, PullMessage is a message of type Sw-PullSnFRequest.</span></span>  
  
5.  <span data-ttu-id="f8eb3-111">Ajoutez une forme envoi pour envoyer le PullMessage (requête de tirage).</span><span class="sxs-lookup"><span data-stu-id="f8eb3-111">Add a Send shape to send the PullMessage (pull request).</span></span>  
  
6.  <span data-ttu-id="f8eb3-112">Ajouter un port requête-réponse pour l’envoi du message par extraction de données et pour recevoir une réponse par extraction de données avec la liaison dynamique.</span><span class="sxs-lookup"><span data-stu-id="f8eb3-112">Add a request-response port for sending the pull message and for receiving the pull response with the dynamic binding.</span></span>  
  
7.  <span data-ttu-id="f8eb3-113">Connectez la forme envoi le port créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="f8eb3-113">Connect the Send shape with the port created in the previous step.</span></span>  
  
8.  <span data-ttu-id="f8eb3-114">Ajoutez une forme réception pour recevoir le PullResponse (message de type PullSnFResponse), puis connectez-vous la forme réception avec le port créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="f8eb3-114">Add a Receive shape to receive the PullResponse (message of type PullSnFResponse) and then connect the Receive shape with the port previously created.</span></span>  
  
9. <span data-ttu-id="f8eb3-115">Envoyer la réponse dans le dossier correspondant à l’aide d’une forme envoi.</span><span class="sxs-lookup"><span data-stu-id="f8eb3-115">Send the response to the respective folder using a Send shape.</span></span>  
  
10. <span data-ttu-id="f8eb3-116">Si vous voulez extraire tous les messages, ajoutez toutes ces activités (envoi d’une requête de tirage et recevoir une réponse) dans une boucle.</span><span class="sxs-lookup"><span data-stu-id="f8eb3-116">Add all of these activities (sending a pull request and receiving the response) in a loop if you want to pull all of the messages.</span></span>  
  
11. <span data-ttu-id="f8eb3-117">Ajoutez une forme Expression CheckQueueEmpty à conserver débrancher jusqu'à ce que le délai de la file d’attente est vide.</span><span class="sxs-lookup"><span data-stu-id="f8eb3-117">Add an Expression shape CheckQueueEmpty to keep pulling until the time queue is empty.</span></span> <span data-ttu-id="f8eb3-118">Consultez l’exemple suivant de la forme Expression :</span><span class="sxs-lookup"><span data-stu-id="f8eb3-118">Refer the following Expression Shape sample:</span></span>  
  
    ```  
    PullResponseDoc=PullResponse;  
    PullResponseNode=PullResponseDoc.SelectSingleNode("/Sw-PullSnFResponse/SwGbl-Status/SwGbl-StatusAttributes/SwGbl-Code");  
    if(PullResponseNode !=null && PullResponseNode.InnerText=="Sw.SnF.QueueEmpty")  
    {  
        IsPull=false;  
    }  
  
    ```  
  
12. <span data-ttu-id="f8eb3-119">Ceci permettra de définir la IsPull = false, une fois que la file d’attente est vide.</span><span class="sxs-lookup"><span data-stu-id="f8eb3-119">This will set the IsPull = false, once the queue is empty.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8eb3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8eb3-120">See Also</span></span>  
 [<span data-ttu-id="f8eb3-121">Étape 3 b : lier l’orchestration avec un port d’envoi dynamique pour le scénario (Pull) avant d’et de FileAct</span><span class="sxs-lookup"><span data-stu-id="f8eb3-121">Step 3B: Bind the orchestration with dynamic send port for FileAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3b-bind-orchestration-with-dynamic-send-for-fileact-store-and-forward.md)