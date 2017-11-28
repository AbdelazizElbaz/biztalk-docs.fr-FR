---
title: Fusion de Documents XML | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML, documents
- process management solution tutorial, merging XML documents
ms.assetid: 444c983a-397a-4342-85e1-80bb152986d9
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94684cd9bf1992a592efd7b97c46838c9c9a3134
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="merging-xml-documents"></a><span data-ttu-id="5fa45-102">Fusion de documents XML</span><span class="sxs-lookup"><span data-stu-id="5fa45-102">Merging XML Documents</span></span>
<span data-ttu-id="5fa45-103">Un des messages qui le **OrderBroker** crée d’orchestration est une mise à jour de la base de données de l’historique de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5fa45-103">One of the messages that the **OrderBroker** orchestration creates is one to update the SQL Server history database.</span></span> <span data-ttu-id="5fa45-104">Ce message contient des champs du message de commande, ainsi que du message de commande original.</span><span class="sxs-lookup"><span data-stu-id="5fa45-104">This message contains fields from the order message as well as the original order message.</span></span> <span data-ttu-id="5fa45-105">La commande originale apparaît dans ce message sous la forme d'une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5fa45-105">The original order appears in this message a string.</span></span> <span data-ttu-id="5fa45-106">Celle-ci correspond au type de données de l'historique de commande dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="5fa45-106">This matches the data type for the order history in the database.</span></span>  
  
 <span data-ttu-id="5fa45-107">Il n'est pas possible d'extraire un message, de le convertir en chaîne, puis de placer celle-ci dans un autre message à l'aide d'un mappage.</span><span class="sxs-lookup"><span data-stu-id="5fa45-107">It isn't possible to take a message, convert it to a string, and place it in another message with a map.</span></span> <span data-ttu-id="5fa45-108">L’orchestration utilise une fonction d’assistance, **InsertOrderBody**, pour ajouter le message d’origine de la commande sous forme de chaîne pour le message d’historique de base.</span><span class="sxs-lookup"><span data-stu-id="5fa45-108">The orchestration uses a helper function, **InsertOrderBody**, to add the original order message as a string to the base history message.</span></span>  
  
 <span data-ttu-id="5fa45-109">Le **OrderBroker** orchestration utilise la carte, **CSR_OrderRequest_To_SQLHistoryInsert**, pour convertir le message de commande dans le message d’historique de base.</span><span class="sxs-lookup"><span data-stu-id="5fa45-109">The **OrderBroker** orchestration uses the map, **CSR_OrderRequest_To_SQLHistoryInsert**, to convert the order message into the base history message.</span></span> <span data-ttu-id="5fa45-110">Les informations d’une commande s’affiche en tant qu’attributs d’une **OrderLog** élément.</span><span class="sxs-lookup"><span data-stu-id="5fa45-110">The information for an order appears as attributes of an **OrderLog** element.</span></span> <span data-ttu-id="5fa45-111">Le message original apparaît en tant qu'autre attribut de cet élément.</span><span class="sxs-lookup"><span data-stu-id="5fa45-111">The original message appears as another attribute of this element.</span></span>  
  
 <span data-ttu-id="5fa45-112">Le **InsertOrderBody** méthode prend comme arguments le message d’origine de la commande, le message d’historique de base et retourne le message d’historique complet.</span><span class="sxs-lookup"><span data-stu-id="5fa45-112">The **InsertOrderBody** method takes as arguments the original order message, the base history message, and returns the completed history message.</span></span> <span data-ttu-id="5fa45-113">Le code suivant inclut les portions de la méthode qui insère le message sous la forme d'une chaîne :</span><span class="sxs-lookup"><span data-stu-id="5fa45-113">The following code shows the portions of the method that inserts the message as a string:</span></span>  
  
```  
public static XmlDocument InsertOrderBody( XmlDocument orderDoc,   
                                    XmlDocument historyInsertDoc)  
{  
...  
    XmlNode root = historyInsertDoc.FirstChild;  
  
    //Create a new attribute.  
    XmlNode attr = historyInsertDoc.CreateNode(XmlNodeType.Attribute,  
                                     "OriginalMsg", root.NamespaceURI);  
    attr.Value = orderDoc.OuterXml;  
  
    try  
    {  
        // XPath expression not shown for formatting reasons and  
        // replaces ".." in the following code  
        XmlNode destnode = historyInsertDoc.SelectSingleNode("..");  
        //Add the attribute to the document.  
        destnode.Attributes.SetNamedItem(attr);  
    }  
...  
  
    return historyInsertDoc;  
}  
```  
  
 <span data-ttu-id="5fa45-114">Après avoir vérifié qu’elle a reçu les deux arguments, le **InsertOrderBody** méthode recherche le nœud racine du message de mise à jour de l’historique.</span><span class="sxs-lookup"><span data-stu-id="5fa45-114">After verifying that it received both arguments, the **InsertOrderBody** method finds the root node of the history update message.</span></span> <span data-ttu-id="5fa45-115">Elle crée ensuite un nœud contenant la **OriginalMsg** d’attribut et affecte le message de commande d’origine à la valeur d’attribut.</span><span class="sxs-lookup"><span data-stu-id="5fa45-115">It then creates a node containing the **OriginalMsg** attribute and assigns the original order message to the attribute's value.</span></span> <span data-ttu-id="5fa45-116">À ce stade, le nœud ne fait qu'exister.</span><span class="sxs-lookup"><span data-stu-id="5fa45-116">At this point, the node simply exists.</span></span> <span data-ttu-id="5fa45-117">Il ne fait pas encore partie d'un élément.</span><span class="sxs-lookup"><span data-stu-id="5fa45-117">It is not yet part of a element.</span></span>  
  
 <span data-ttu-id="5fa45-118">Après avoir créé le nœud d'attribut, la méthode recherche le nœud auquel elle joindra l'attribut à l'aide d'une expression XPath.</span><span class="sxs-lookup"><span data-stu-id="5fa45-118">After creating the attribute node, the method finds the node where it will attach the attribute using an XPath expression.</span></span> <span data-ttu-id="5fa45-119">Après avoir localisé le nœud, la méthode ajoute le nœud d'attribut à la collection d'attributs du nœud.</span><span class="sxs-lookup"><span data-stu-id="5fa45-119">After it locates the node, the method adds the attribute node to the attributes collection of the node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fa45-120">Bien que le **OriginalMsg** initialement, les attributs n’existent pas dans le message d’historique de base, il est, bien entendu, spécifié dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="5fa45-120">Although the **OriginalMsg** attribute does not initially exist in the base history message, it is, of course, specified in the schema.</span></span> <span data-ttu-id="5fa45-121">Les éléments XML que vous ajoutez à vos messages dans le code doivent être spécifiés dans les schémas de ces messages.</span><span class="sxs-lookup"><span data-stu-id="5fa45-121">XML elements that you add to your messages in code should be specified in the schemas for those messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa45-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fa45-122">See Also</span></span>  
 [<span data-ttu-id="5fa45-123">Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="5fa45-123">Implementation Highlights of the Business Process Management Solution</span></span>](../core/implementation-highlights-of-the-business-process-management-solution.md)