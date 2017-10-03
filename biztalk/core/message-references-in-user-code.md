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
# <a name="message-references-in-user-code"></a>Références de message dans le code utilisateur
Lors de la création d'un message, une de ses représentations figure dans la base de données MessageBox et l'autre dans la mémoire de l'ordinateur. Si vous affectez un message en transmettant une référence du message à un objet .NET ou à un assembly externe, et que l'objet .NET ou l'assembly externe modifie sa représentation dans la mémoire de l'ordinateur, le moteur d'orchestration BizTalk n'est pas informé de cette modification.  
  
 De plus, le moteur d'orchestration n'invalide pas les données de partie du message contenues dans la représentation de la base de données MessageBox. Les modes de représentation de ces données sont les suivants :  
  
-   Représentation XmlDocument  
  
-   Représentation objet  
  
-   Représentation flux  
  
-   Représentation UnderlyingPart  
  
 Le mode de représentation des données de partie de message dans la mémoire dépend de la construction du message et du type (classe .NET ou schéma XSD). Toutefois, la représentation UnderlyingPart est toujours un flux pointant sur la base de données MessageBox. Les messages de BizTalk Server ne pouvant plus être modifiés après leur validation dans la base de données MessageBox, le moteur d'orchestration utilise la représentation de la base de données MessageBox pour référencer les données de partie des messages.  
  
> [!NOTE]
>  Il se peut qu'un message créé dispose déjà d'une représentation dans la base de données MessageBox si vous assignez les parties d'un message déjà validé.  
  
 Par exemple, le code suivant permet d'envoyer les données UnderlyingPart depuis la représentation de la base de données MessageBox :  
  
```  
// In this example, assume m1 is committed to the MessageBox  
Construct m2 {   
               m2 = m1; // m2’s part data representation is the UnderlyingPart data of m1  
               m2(myContextProperty) = “123”; // m2’s part data representation is still the UnderlyingPart data of m1  
               A.test(m2.part); // orchestration engine does not invalidate the UnderlyingPart MessageBox representation  
             }  
Send(p.o, m2);  
```  
  
 Au lieu d'utiliser le code utilisateur précédent, utilisez le code similaire à celui qui suit pour retourner un document XmlDocument pour une variable XLANG de message :  
  
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