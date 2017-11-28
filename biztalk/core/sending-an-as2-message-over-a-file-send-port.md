---
title: "Envoyer un Message AS2 via un Port d’envoi FILE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c5ce9ff-fd73-4d5f-9b16-387c1e520c3a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 555066cb81eabe7328734e73fd9598fbd2cd418a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sending-an-as2-message-over-a-file-send-port"></a><span data-ttu-id="7a037-102">Envoi d'un message AS2 via un port d'envoi FILE</span><span class="sxs-lookup"><span data-stu-id="7a037-102">Sending an AS2 Message over a FILE Send Port</span></span>
<span data-ttu-id="7a037-103">Les messages AS2 sont habituellement envoyés via un adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="7a037-103">AS2 messages are normally sent over an HTTP adapter.</span></span> <span data-ttu-id="7a037-104">Vous pouvez toutefois les envoyer via un adaptateur FILE si vous créez des composants personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7a037-104">You can, however, send AS2 messages over a FILE adapter if you create custom components.</span></span> <span data-ttu-id="7a037-105">Cette rubrique décrit le fonctionnement d'une telle solution et fournit un exemple de code pour la solution.</span><span class="sxs-lookup"><span data-stu-id="7a037-105">This topic describes how such a solution would work and provides sample code for the solution.</span></span>  
  
 <span data-ttu-id="7a037-106">Lorsque les messages AS2 sont envoyés via HTTP, l'encodeur AS2 dans le pipeline d'envoi renseigne la propriété de contexte `HTTP.UserHttpHeaders` à l'aide des en-têtes HTTP (et AS2) nécessaires à l'envoi du message.</span><span class="sxs-lookup"><span data-stu-id="7a037-106">When AS2 messages are sent over HTTP, the AS2 Encoder in the send pipeline populates the `HTTP.UserHttpHeaders` context property with the HTTP (and AS2) headers required for sending the message.</span></span> <span data-ttu-id="7a037-107">Il extrait ces en-têtes de la propriété de contexte `HTTP.UserHttpHeaders` existante, de propriétés de contexte distinctes ou de propriétés d'accord (dans cet ordre).</span><span class="sxs-lookup"><span data-stu-id="7a037-107">It takes these headers either from the existing `HTTP.UserHttpHeaders` context property, from separate context properties, or from agreement properties (in that order of precedence).</span></span> <span data-ttu-id="7a037-108">L'adaptateur HTTP dans le port d'envoi écrit les en-têtes dans le message, puis envoie le message via HTTP.</span><span class="sxs-lookup"><span data-stu-id="7a037-108">The HTTP adapter in the send port will write the headers to the message, and send the message over HTTP.</span></span>  
  
 <span data-ttu-id="7a037-109">Si vous utilisez un adaptateur FILE au lieu d'un adaptateur HTTP dans le port d'envoi, les valeurs d'en-tête dans la propriété de contexte `HTTP.UserHttpHeaders` ne sont pas écrites dans le message.</span><span class="sxs-lookup"><span data-stu-id="7a037-109">If you use a FILE adapter instead of an HTTP adapter in the send port, the header values in the `HTTP.UserHttpHeaders` context property will not be written to the message.</span></span> <span data-ttu-id="7a037-110">Vous devez créer un composant de pipeline personnalisé pour ajouter les en-têtes dans la propriété de contexte `HTTP.UserHttpHeaders` au message.</span><span class="sxs-lookup"><span data-stu-id="7a037-110">You have to create a custom pipeline component to prepend the headers in `HTTP.UserHttpHeaders` to the message.</span></span> <span data-ttu-id="7a037-111">Le message peut ensuite être déposé dans un dossier par l'adaptateur FILE. Il s'agit d'un message AS2 incluant les en-têtes HTTP requis.</span><span class="sxs-lookup"><span data-stu-id="7a037-111">The message can then be dropped into a folder by the FILE adapter, and will be an AS2 message that includes the required HTTP headers.</span></span>  
  
 <span data-ttu-id="7a037-112">Il se peut que vous deviez également créer un composant personnalisé afin que tous les en-têtes AS2 soient inclus dans la propriété de contexte `HTTP.UserHttpHeaders`.</span><span class="sxs-lookup"><span data-stu-id="7a037-112">You may also need to create a custom component to ensure that all the AS2 headers are included in the `HTTP.UserHttpHeaders` context property.</span></span> <span data-ttu-id="7a037-113">Vous pouvez créer une orchestration personnalisée ou un composant de pipeline personnalisé avant l'encodeur AS2 pour définir les propriétés de contexte utilisées par ce dernier pour construire la propriété de contexte `HTTP.UserHttpHeaders`.</span><span class="sxs-lookup"><span data-stu-id="7a037-113">You can create either a custom orchestration, or a custom pipeline component before the AS2Encoder, to set the context properties that the AS2 Encoder uses to build `HTTP.UserHttpHeaders`.</span></span>  
  
## <a name="writing-headers-to-an-as2-message"></a><span data-ttu-id="7a037-114">Écriture des en-têtes dans un message AS2</span><span class="sxs-lookup"><span data-stu-id="7a037-114">Writing Headers to an AS2 Message</span></span>  
 <span data-ttu-id="7a037-115">Pour générer un message AS2 à l'aide d'un adaptateur FILE plutôt que d'un adaptateur HTTP, ajoutez un composant de pipeline personnalisé après l'encodeur AS2 dans un pipeline d'envoi AS2 personnalisé.</span><span class="sxs-lookup"><span data-stu-id="7a037-115">To generate an AS2 message using a FILE adapter, rather than an HTTP adapter, add a custom pipeline component after the AS2 Encoder in a custom AS2 send pipeline.</span></span> <span data-ttu-id="7a037-116">Incluez le code dans le composant de pipeline personnalisé qui écrit les en-têtes à partir de la propriété de contexte `HTTP.UserHttpHeaders` dans le message.</span><span class="sxs-lookup"><span data-stu-id="7a037-116">Include code in the custom pipeline component that writes the headers from the `HTTP.UserHttpHeaders` context property into the message.</span></span> <span data-ttu-id="7a037-117">Voici un exemple de code :</span><span class="sxs-lookup"><span data-stu-id="7a037-117">An example is the following sample code:</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext pContext, IBaseMessage pInMsg)  
        {  
            IPipelineContext pipelineContext = pContext;  
            IBaseMessage baseMessage = pInMsg;  
  
            //Prepend Headers  
            MemoryStream ms = new MemoryStream();  
            string strName = "UserHttpHeaders";  
            string strValue = (string)baseMessage.Context.Read(strName,  
              "http://schemas.microsoft.com/BizTalk/2003/  
              http-properties");  
  
            //Leave an empty line between the headers and the body  
            strValue += "\r\n";  
            ms.Write(Encoding.ASCII.GetBytes(strValue), 0,   
               Encoding.ASCII.GetByteCount(strValue));  
  
            //Append Body  
            Stream sr = baseMessage.BodyPart.Data;  
  
            //Read the body of the message and append it to the memory   
              stream containing the headers  
            int size = 1024;  
            byte[] buffer = new byte[size];  
            while (0 != (size = sr.Read(buffer, 0, buffer.Length)))  
            {  
                ms.Write(buffer, 0, size);  
            }  
  
            //Set the body of the message to the new memory stream  
            baseMessage.BodyPart.Data = ms;  
  
            //Rewind the stream  
            ms.Seek(0, SeekOrigin.Begin);  
  
            return baseMessage;  
        }  
```  
  
## <a name="promoting-as2-header-context-properties"></a><span data-ttu-id="7a037-118">Promotion des propriétés de contexte d'en-tête AS2</span><span class="sxs-lookup"><span data-stu-id="7a037-118">Promoting AS2 Header Context Properties</span></span>  
 <span data-ttu-id="7a037-119">Vous pouvez promouvoir les propriétés d'en-tête AS2 dans le contexte d'un message à l'aide d'une orchestration personnalisée ou d'un composant de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="7a037-119">You can promote AS2 header properties into the context of a message using either a custom orchestration or a custom pipeline component.</span></span>  
  
 <span data-ttu-id="7a037-120">Pour promouvoir les propriétés d'en-tête AS2 à l'aide d'un composant de pipeline personnalisé, ajoutez un composant de pipeline personnalisé avant l'encodeur AS2 dans un pipeline d'envoi AS2 personnalisé.</span><span class="sxs-lookup"><span data-stu-id="7a037-120">To promote AS2 header properties using a custom pipeline component, add a custom pipeline component before the AS2 Encoder in a custom AS2 send pipeline.</span></span> <span data-ttu-id="7a037-121">Vous pouvez utiliser l'exemple de code fourni plus haut pour écrire les en-têtes à partir de la propriété de contexte `HTTP.UserHttpHeaders` dans le message. Vous devez toutefois remplacer la méthode Read par la méthode Promote, et indiquer le nom, la valeur et l'espace de noms de la propriété de contexte à promouvoir.</span><span class="sxs-lookup"><span data-stu-id="7a037-121">You can use code from the sample code shown above for writing headers from `HTTP.UserHttpHeaders` into the message, with the exception that you would replace the Read method with a Promote method, providing the name, value, and namespace of the context property to be promoted.</span></span>  
  
 <span data-ttu-id="7a037-122">Pour promouvoir les propriétés d'en-tête AS2 à l'aide d'une orchestration personnalisée, créez une orchestration avec un port de réception FILE, une forme Construire un message et un port d'envoi FILE.</span><span class="sxs-lookup"><span data-stu-id="7a037-122">To promote AS2 header properties using a custom orchestration, create an orchestration with a FILE receive port, a Construct Message shape, and a FILE send port.</span></span> <span data-ttu-id="7a037-123">Dans la forme Construire un message, ajoutez le code qui définit les propriétés promues contenant les en-têtes AS2.</span><span class="sxs-lookup"><span data-stu-id="7a037-123">To the Construct Message shape, add code setting the promoted properties that contain the AS2 headers.</span></span> <span data-ttu-id="7a037-124">Vous devez ajouter une référence à `Microsoft.BizTalk.HttpTransport.dll` dans l'orchestration personnalisée.</span><span class="sxs-lookup"><span data-stu-id="7a037-124">You must add a reference to `Microsoft.BizTalk.HttpTransport.dll` in the custom orchestration.</span></span>  
  
 <span data-ttu-id="7a037-125">Les espaces de noms pour les en-têtes HTTP sont `http://schemas.microsoft.com/BizTalk/2003/http-properties` pour les en-têtes HTTP non-AS2 et `http://schemas.microsoft.com/BizTalk/2003/as2-properties` pour les en-têtes AS2.</span><span class="sxs-lookup"><span data-stu-id="7a037-125">The namespaces for HTTP headers is `http://schemas.microsoft.com/BizTalk/2003/http-properties` for non-AS2 HTTP headers and `http://schemas.microsoft.com/BizTalk/2003/as2-properties` for AS2 headers.</span></span>  
  
 <span data-ttu-id="7a037-126">L'exemple de code suivant illustre la promotion des propriétés d'en-tête AS2 dans la forme Construire un message d'une orchestration.</span><span class="sxs-lookup"><span data-stu-id="7a037-126">The following sample code shows how to promote AS2 header properties in the Construct Message shape of an orchestration.</span></span> <span data-ttu-id="7a037-127">Ce code promeut les en-têtes AS2 pour un MDN.</span><span class="sxs-lookup"><span data-stu-id="7a037-127">This code promotes AS2 headers for an MDN.</span></span>  
  
```  
Message_2=new System.Xml.XmlDocument();  
Message_2=Message_1;  
Message_2(EdiIntAS.IsAS2PayloadMessage)=false;  
Message_2(EdiIntAS.IsAS2AsynchronousMdn)=true;  
Message_2(EdiIntAS.IsAS2MdnResponseMessage)=true;  
Message_2(EdiIntAS.SendMDN)=true;  
Message_2(EdiIntAS.IsAS2MessageSigned)=false;  
Message_2(EdiIntAS.AS2To)="Party1";  
Message_2(EdiIntAS.AS2From)="Home";  
Message_2(EdiIntAS.MessageId)="123456";  
Message_2(EdiIntAS.OriginalMessageId)="2123456";  
Message_2(HTTP.UserHttpHeaders)="Message1-Id: xyz\r\nMyHeader: MyValue";  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a037-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a037-128">See Also</span></span>  
 [<span data-ttu-id="7a037-129">Développement et la configuration des Solutions AS2 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7a037-129">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)