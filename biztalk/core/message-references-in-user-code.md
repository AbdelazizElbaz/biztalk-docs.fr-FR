---
title: "Message de références dans le Code utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a1584be-35fd-4dc2-a5a9-559300e67e0e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 264f50da516f44d8fc87186614a79bb81aaf77ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-references-in-user-code"></a><span data-ttu-id="301ec-102">Références de message dans le code utilisateur</span><span class="sxs-lookup"><span data-stu-id="301ec-102">Message References in User Code</span></span>
<span data-ttu-id="301ec-103">Lors de la création d'un message, une de ses représentations figure dans la base de données MessageBox et l'autre dans la mémoire de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="301ec-103">When a message is constructed, a representation of the message is in the MessageBox database and another representation is in memory on the computer.</span></span> <span data-ttu-id="301ec-104">Si vous affectez un message en transmettant une référence du message à un objet .NET ou à un assembly externe, et que l'objet .NET ou l'assembly externe modifie sa représentation dans la mémoire de l'ordinateur, le moteur d'orchestration BizTalk n'est pas informé de cette modification.</span><span class="sxs-lookup"><span data-stu-id="301ec-104">If you make the message assignment by passing a message reference to a .NET object or to an external assembly, and then the .NET object or the external assembly modifies the representation in memory on the computer, the BizTalk Orchestration Engine is not aware of the modification.</span></span>  
  
 <span data-ttu-id="301ec-105">De plus, le moteur d'orchestration n'invalide pas les données de partie du message contenues dans la représentation de la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="301ec-105">Moreover, the orchestration engine does not invalidate the message part data that is in the representation in the MessageBox database.</span></span> <span data-ttu-id="301ec-106">Les modes de représentation de ces données sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="301ec-106">Message part data has the following modes of representation:</span></span>  
  
-   <span data-ttu-id="301ec-107">Représentation XmlDocument</span><span class="sxs-lookup"><span data-stu-id="301ec-107">XmlDocument representation</span></span>  
  
-   <span data-ttu-id="301ec-108">Représentation objet</span><span class="sxs-lookup"><span data-stu-id="301ec-108">Object representation</span></span>  
  
-   <span data-ttu-id="301ec-109">Représentation flux</span><span class="sxs-lookup"><span data-stu-id="301ec-109">Stream representation</span></span>  
  
-   <span data-ttu-id="301ec-110">Représentation UnderlyingPart</span><span class="sxs-lookup"><span data-stu-id="301ec-110">UnderlyingPart representation</span></span>  
  
 <span data-ttu-id="301ec-111">Le mode de représentation des données de partie de message dans la mémoire dépend de la construction du message et du type (classe .NET ou schéma XSD).</span><span class="sxs-lookup"><span data-stu-id="301ec-111">How the message part data is represented in memory depends on the message construction and whether the type is a .NET class or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="301ec-112">Toutefois, la représentation UnderlyingPart est toujours un flux pointant sur la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="301ec-112">However, the UnderlyingPart representation is always a stream pointing into the MessageBox database.</span></span> <span data-ttu-id="301ec-113">Les messages de BizTalk Server ne pouvant plus être modifiés après leur validation dans la base de données MessageBox, le moteur d'orchestration utilise la représentation de la base de données MessageBox pour référencer les données de partie des messages.</span><span class="sxs-lookup"><span data-stu-id="301ec-113">Because messages in BizTalk Server are immutable after the message is committed to the MessageBox database, the orchestration engine uses the representation in the MessageBox database to reference message part data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="301ec-114">Il se peut qu'un message créé dispose déjà d'une représentation dans la base de données MessageBox si vous assignez les parties d'un message déjà validé.</span><span class="sxs-lookup"><span data-stu-id="301ec-114">A constructed message may already have a representation in the MessageBox database if you assign parts from a message that is already committed.</span></span>  
  
 <span data-ttu-id="301ec-115">Par exemple, le code suivant permet d'envoyer les données UnderlyingPart depuis la représentation de la base de données MessageBox :</span><span class="sxs-lookup"><span data-stu-id="301ec-115">For example, the following code sends the UnderlyingPart data from the representation in the MessageBox database:</span></span>  
  
```  
// In this example, assume m1 is committed to the MessageBox  
Construct m2 {   
               m2 = m1; // m2’s part data representation is the UnderlyingPart data of m1  
               m2(myContextProperty) = “123”; // m2’s part data representation is still the UnderlyingPart data of m1  
               A.test(m2.part); // orchestration engine does not invalidate the UnderlyingPart MessageBox representation  
             }  
Send(p.o, m2);  
```  
  
 <span data-ttu-id="301ec-116">Au lieu d'utiliser le code utilisateur précédent, utilisez le code similaire à celui qui suit pour retourner un document XmlDocument pour une variable XLANG de message :</span><span class="sxs-lookup"><span data-stu-id="301ec-116">Instead of using the preceding user code, you can use code that is similar to the following to return an XmlDocument document to a Message XLANG variable:</span></span>  
  
```  
Void A.test(ref XmlDocument xd) {…}  
XmlDocument B.test(XmlDocument xd) {…}  
construct m2 {  
               m2 = m1;  
               m2(myContextProperty) = “123”; // m2’s part data representation is the UnderlyingPart data of m1  
               A.test(ref m2.part); // orchestration engine has enough information to know it has to invalidate the UnderlyingPart MessageBox representation  
               // or  
               m2.part = B.test(m2.part); // orchestration engine has enough information to know it has to invalidate the UnderlyingPart MessageBox representation  
             }  
```