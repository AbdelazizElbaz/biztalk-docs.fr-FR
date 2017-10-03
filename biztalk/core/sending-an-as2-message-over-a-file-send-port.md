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
# <a name="sending-an-as2-message-over-a-file-send-port"></a>Envoi d'un message AS2 via un port d'envoi FILE
Les messages AS2 sont habituellement envoyés via un adaptateur HTTP. Vous pouvez toutefois les envoyer via un adaptateur FILE si vous créez des composants personnalisés. Cette rubrique décrit le fonctionnement d'une telle solution et fournit un exemple de code pour la solution.  
  
 Lorsque les messages AS2 sont envoyés via HTTP, l'encodeur AS2 dans le pipeline d'envoi renseigne la propriété de contexte `HTTP.UserHttpHeaders` à l'aide des en-têtes HTTP (et AS2) nécessaires à l'envoi du message. Il extrait ces en-têtes de la propriété de contexte `HTTP.UserHttpHeaders` existante, de propriétés de contexte distinctes ou de propriétés d'accord (dans cet ordre). L'adaptateur HTTP dans le port d'envoi écrit les en-têtes dans le message, puis envoie le message via HTTP.  
  
 Si vous utilisez un adaptateur FILE au lieu d'un adaptateur HTTP dans le port d'envoi, les valeurs d'en-tête dans la propriété de contexte `HTTP.UserHttpHeaders` ne sont pas écrites dans le message. Vous devez créer un composant de pipeline personnalisé pour ajouter les en-têtes dans la propriété de contexte `HTTP.UserHttpHeaders` au message. Le message peut ensuite être déposé dans un dossier par l'adaptateur FILE. Il s'agit d'un message AS2 incluant les en-têtes HTTP requis.  
  
 Il se peut que vous deviez également créer un composant personnalisé afin que tous les en-têtes AS2 soient inclus dans la propriété de contexte `HTTP.UserHttpHeaders`. Vous pouvez créer une orchestration personnalisée ou un composant de pipeline personnalisé avant l'encodeur AS2 pour définir les propriétés de contexte utilisées par ce dernier pour construire la propriété de contexte `HTTP.UserHttpHeaders`.  
  
## <a name="writing-headers-to-an-as2-message"></a>Écriture des en-têtes dans un message AS2  
 Pour générer un message AS2 à l'aide d'un adaptateur FILE plutôt que d'un adaptateur HTTP, ajoutez un composant de pipeline personnalisé après l'encodeur AS2 dans un pipeline d'envoi AS2 personnalisé. Incluez le code dans le composant de pipeline personnalisé qui écrit les en-têtes à partir de la propriété de contexte `HTTP.UserHttpHeaders` dans le message. Voici un exemple de code :  
  
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
  
## <a name="promoting-as2-header-context-properties"></a>Promotion des propriétés de contexte d'en-tête AS2  
 Vous pouvez promouvoir les propriétés d'en-tête AS2 dans le contexte d'un message à l'aide d'une orchestration personnalisée ou d'un composant de pipeline personnalisé.  
  
 Pour promouvoir les propriétés d'en-tête AS2 à l'aide d'un composant de pipeline personnalisé, ajoutez un composant de pipeline personnalisé avant l'encodeur AS2 dans un pipeline d'envoi AS2 personnalisé. Vous pouvez utiliser l'exemple de code fourni plus haut pour écrire les en-têtes à partir de la propriété de contexte `HTTP.UserHttpHeaders` dans le message. Vous devez toutefois remplacer la méthode Read par la méthode Promote, et indiquer le nom, la valeur et l'espace de noms de la propriété de contexte à promouvoir.  
  
 Pour promouvoir les propriétés d'en-tête AS2 à l'aide d'une orchestration personnalisée, créez une orchestration avec un port de réception FILE, une forme Construire un message et un port d'envoi FILE. Dans la forme Construire un message, ajoutez le code qui définit les propriétés promues contenant les en-têtes AS2. Vous devez ajouter une référence à `Microsoft.BizTalk.HttpTransport.dll` dans l'orchestration personnalisée.  
  
 Les espaces de noms pour les en-têtes HTTP sont `http://schemas.microsoft.com/BizTalk/2003/http-properties` pour les en-têtes HTTP non-AS2 et `http://schemas.microsoft.com/BizTalk/2003/as2-properties` pour les en-têtes AS2.  
  
 L'exemple de code suivant illustre la promotion des propriétés d'en-tête AS2 dans la forme Construire un message d'une orchestration. Ce code promeut les en-têtes AS2 pour un MDN.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions AS2 BizTalk Server](../core/developing-and-configuring-biztalk-server-as2-solutions.md)