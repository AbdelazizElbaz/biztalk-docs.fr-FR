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
# <a name="merging-xml-documents"></a>Fusion de documents XML
Un des messages qui le **OrderBroker** crée d’orchestration est une mise à jour de la base de données de l’historique de SQL Server. Ce message contient des champs du message de commande, ainsi que du message de commande original. La commande originale apparaît dans ce message sous la forme d'une chaîne. Celle-ci correspond au type de données de l'historique de commande dans la base de données.  
  
 Il n'est pas possible d'extraire un message, de le convertir en chaîne, puis de placer celle-ci dans un autre message à l'aide d'un mappage. L’orchestration utilise une fonction d’assistance, **InsertOrderBody**, pour ajouter le message d’origine de la commande sous forme de chaîne pour le message d’historique de base.  
  
 Le **OrderBroker** orchestration utilise la carte, **CSR_OrderRequest_To_SQLHistoryInsert**, pour convertir le message de commande dans le message d’historique de base. Les informations d’une commande s’affiche en tant qu’attributs d’une **OrderLog** élément. Le message original apparaît en tant qu'autre attribut de cet élément.  
  
 Le **InsertOrderBody** méthode prend comme arguments le message d’origine de la commande, le message d’historique de base et retourne le message d’historique complet. Le code suivant inclut les portions de la méthode qui insère le message sous la forme d'une chaîne :  
  
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
  
 Après avoir vérifié qu’elle a reçu les deux arguments, le **InsertOrderBody** méthode recherche le nœud racine du message de mise à jour de l’historique. Elle crée ensuite un nœud contenant la **OriginalMsg** d’attribut et affecte le message de commande d’origine à la valeur d’attribut. À ce stade, le nœud ne fait qu'exister. Il ne fait pas encore partie d'un élément.  
  
 Après avoir créé le nœud d'attribut, la méthode recherche le nœud auquel elle joindra l'attribut à l'aide d'une expression XPath. Après avoir localisé le nœud, la méthode ajoute le nœud d'attribut à la collection d'attributs du nœud.  
  
> [!NOTE]
>  Bien que le **OriginalMsg** initialement, les attributs n’existent pas dans le message d’historique de base, il est, bien entendu, spécifié dans le schéma. Les éléments XML que vous ajoutez à vos messages dans le code doivent être spécifiés dans les schémas de ces messages.  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md)