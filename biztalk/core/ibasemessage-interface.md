---
title: Interface IBaseMessage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10bfb95c-aef5-46ba-ba0e-9961833f27a3
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7de478b27105ee6c01d582aa9b728bd0496d0487
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ibasemessage-interface"></a><span data-ttu-id="b648a-102">Interface IBaseMessage</span><span class="sxs-lookup"><span data-stu-id="b648a-102">IBaseMessage Interface</span></span>
<span data-ttu-id="b648a-103">Lorsqu’un adaptateur de réception accepte un paquet de données entrant via son protocole, il utilise le **IBaseMessage** interface pour créer un message à transmettre au moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="b648a-103">When a receive adapter accepts an incoming data packet through its protocol, it uses the **IBaseMessage** interface to create a message to pass to the Messaging Engine.</span></span> <span data-ttu-id="b648a-104">Cette interface permet de représenter tous les messages.</span><span class="sxs-lookup"><span data-stu-id="b648a-104">All messages are represented by using this interface.</span></span>  
  
 <span data-ttu-id="b648a-105">Un message possède une ou plusieurs parties représentées par le **IBaseMessagePart** interface.</span><span class="sxs-lookup"><span data-stu-id="b648a-105">A message has one or more message parts represented by the **IBaseMessagePart** interface.</span></span> <span data-ttu-id="b648a-106">Chaque partie du message a une référence à ses données via un **IStream** pointeur d’interface.</span><span class="sxs-lookup"><span data-stu-id="b648a-106">Each message part has a reference to its data through an **IStream** interface pointer.</span></span> <span data-ttu-id="b648a-107">Le contexte d’un message est représenté par son **IBaseMessageContext** interface.</span><span class="sxs-lookup"><span data-stu-id="b648a-107">The context of a message is represented by its **IBaseMessageContext** interface.</span></span> <span data-ttu-id="b648a-108">La figure suivante illustre le modèle d'objet Message de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b648a-108">The following figure illustrates the BizTalk message object model.</span></span>  
  
 ![](../core/media/ibasemessagestructure.gif "IBaseMessageStructure")  
  
 <span data-ttu-id="b648a-109">Le contexte de message est un dictionnaire codé par une combinaison du nom de la propriété et de l'espace de noms de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b648a-109">The message context is a dictionary that is keyed on a combination of the property name and the property namespace.</span></span> <span data-ttu-id="b648a-110">Cela empêche toute collision entre des propriétés aux noms similaires provenant de sources diverses, comme les propriétés du système [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les propriétés personnalisées de l'adaptateur, par exemple.</span><span class="sxs-lookup"><span data-stu-id="b648a-110">This prevents collisions between similarly named properties from different sources, for example, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system properties and custom adapter properties.</span></span> <span data-ttu-id="b648a-111">Les valeurs de ces propriétés sont du type .NET **objet**, mais en réalité ces propriétés sont des variantes.</span><span class="sxs-lookup"><span data-stu-id="b648a-111">The values for these properties are of the .NET type **object**, but in fact these properties are VARIANTs.</span></span>  
  
 <span data-ttu-id="b648a-112">Chaque partie comporte également un contexte de partie sous la forme d'un dictionnaire, mais sans la notion d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="b648a-112">Each part has a part context that is also a dictionary but without the notion of a namespace.</span></span> <span data-ttu-id="b648a-113">La valeur d'un contexte de partie correspond aux métadonnées faisant référence aux données de cette partie.</span><span class="sxs-lookup"><span data-stu-id="b648a-113">The value of a part context is metadata referring to the data for that part.</span></span> <span data-ttu-id="b648a-114">Ceci est la **Charset** propriété qui spécifie le jeu de caractères utilisé pour encoder le message.</span><span class="sxs-lookup"><span data-stu-id="b648a-114">An example of this is the **Charset** property that specifies the character set used for encoding the message.</span></span>  
  
 <span data-ttu-id="b648a-115">Les propriétés peuvent être soit écrites, soit lues dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="b648a-115">Properties may be written to and read from the message context.</span></span> <span data-ttu-id="b648a-116">Elles peuvent également être promues et utilisées pour le routage des messages.</span><span class="sxs-lookup"><span data-stu-id="b648a-116">They may also be promoted to be used for message routing.</span></span> <span data-ttu-id="b648a-117">Cela signifie qu'elles sont écrites au sein des métadonnées qui circulent avec le message.</span><span class="sxs-lookup"><span data-stu-id="b648a-117">Being promoted means they are written as a part of metadata that flows with the message.</span></span> <span data-ttu-id="b648a-118">Une propriété promue permet à sa valeur d'être utilisée dans la création de filtres des expressions sur les orchestrations et les ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="b648a-118">A promoted property allows its value to be used in the creation of filter expressions on send ports and orchestrations.</span></span> <span data-ttu-id="b648a-119">Les composants en aval et le code utilisateur des orchestrations peuvent lire les propriétés promues ainsi que leur donner de nouvelles valeurs.</span><span class="sxs-lookup"><span data-stu-id="b648a-119">Downstream components and user code in orchestrations may read promoted properties and also write new values to them.</span></span>  
  
 <span data-ttu-id="b648a-120">Après qu'une propriété promue a été associée à un abonnement existant et utilisée pour le routage d'un message, la propriété est rétrogradée pour empêcher les correspondances cycliques d'abonnement.</span><span class="sxs-lookup"><span data-stu-id="b648a-120">After a promoted property has been matched to an existing subscription and used to route a message, the property is demoted to prevent cyclic subscription matches.</span></span> <span data-ttu-id="b648a-121">Une propriété rétrogradée reste dans le contexte du message en tant que métadonnée mais perd son état de propriété promue.</span><span class="sxs-lookup"><span data-stu-id="b648a-121">A demoted property remains on the message context as metadata but loses its promoted status.</span></span>  
  
 <span data-ttu-id="b648a-122">**Conseil pour l’implémentation :** les propriétés de contexte de Message sont chargées en mémoire au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b648a-122">**Implementation Tip:** Message context properties are loaded into memory at run time.</span></span> <span data-ttu-id="b648a-123">Il ne faut pas insérer de grandes quantités de données dans le contexte du message car cela risquerait d'empêcher la prise en charge des messages volumineux par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b648a-123">Very large pieces of data should not be written to the message context because this could potentially break the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] large message support.</span></span> <span data-ttu-id="b648a-124">Les objets peuvent être sérialisés dans le contexte du message qu’ils implémentent le **IPersistStream** interface.</span><span class="sxs-lookup"><span data-stu-id="b648a-124">Objects may be serialized into the message context providing they implement the **IPersistStream** interface.</span></span> <span data-ttu-id="b648a-125">D'autre part, les propriétés promues sont limitées à 255 caractères.</span><span class="sxs-lookup"><span data-stu-id="b648a-125">Also, promoted properties are limited to 255 characters.</span></span>  
  
 <span data-ttu-id="b648a-126">Il faut toujours utiliser la fabrique de messages pour créer de nouveaux messages.</span><span class="sxs-lookup"><span data-stu-id="b648a-126">The message factory should always be used to create new messages.</span></span>  <span data-ttu-id="b648a-127">Le fragment de code suivant montre comment créer un nouveau message BizTalk à partir du flux de données reçu par l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="b648a-127">The following code fragment illustrates how to create a new BizTalk message from the data stream received by the adapter.</span></span>  
  
```  
using Microsoft.BizTalk.Message.Interop;  
  
IBaseMessage CreateMessage( Stream s, IBaseMessageFactory msgFactory )  
{  
IBaseMessage msg = null;  
IBaseMessagePart part = msgFactory.CreateMessagePart();  
part.Data = s;  
msg = msgFactory.CreateMessage();  
msg.AddPart("body", part, true);  
return msg;  
}  
```