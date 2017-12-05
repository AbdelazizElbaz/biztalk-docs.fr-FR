---
title: "En spécifiant le corps du Message pour les adaptateurs WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF adapters, SOAP messages
- messages, WCF adapters
- WCF adapters, message bodies
- SOAP messages, WCF adapters
ms.assetid: b20364b7-0365-4636-b4d6-bde9c69b8dcb
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 109ad486baa542aff3cd1c4a44804ff2fd79aac5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="specifying-the-message-body-for-the-wcf-adapters"></a>Spécification du corps de message pour les adaptateurs WCF
Vous pouvez utiliser la **Messages** onglet dans les adaptateurs WCF pour spécifier la manière dont le corps du message BizTalk est extrait à partir d’un message SOAP entrant, et comment les corps du message BizTalk est placé dans un message SOAP sortant.  
  
## <a name="specifying-how-the-biztalk-message-body-is-extracted-from-an-incoming-soap-message"></a>Spécification de la manière dont le corps du message BizTalk est extrait d'un message SOAP entrant  
 Vous pouvez contrôler la création du corps du message BizTalk entrant à partir de messages SOAP entrant par l'intermédiaire d'adaptateurs WCF. Les illustrations suivantes montrent le **Messages** onglets de WCF-NetNamedPipe adaptateurs de réception et adaptateur d’envoi à titre d’exemple.  
  
 ![L’onglet des Messages WCF des adaptateurs de réception](../core/media/abbaccfc-092c-42c6-9207-fa1af28912ac.gif "abbaccfc-092c-42c6-9207-fa1af28912ac")  
  
 ![L’onglet des Messages WCF des adaptateurs d’envoi](../core/media/58e1d490-5bd9-4571-87b1-4dea6dbfe2de.gif "58e1d490-5bd9-4571-87b1-4dea6dbfe2de")  
  
 Pour spécifier comment créer le corps du message BizTalk, sélectionnez une des options suivantes dans le **le corps du message BizTalk entrant** section dans les figures précédentes :  
  
-   **: Enveloppe \<soap : Envelope\>**. Utilise le protocole SOAP **enveloppe** élément d’un message entrant pour créer le corps du message BizTalk. La totalité du message entrant devient le corps du message BizTalk. Utilisez cette option pour créer le corps du message BizTalk incorporant tous les en-têtes.  
  
    > [!NOTE]
    >  Les en-têtes SOAP sont placés dans le contexte de message, mais ils ne sont pas promus automatiquement. La promotion peut être effectuée dans un composant de pipeline personnalisé.  
  
-   **Corps : contenu de \<soap : Body\> élément**. Utilise le contenu de SOAP **corps** élément d’un message entrant pour créer le corps du message BizTalk. Si l'élément **Body** a plusieurs éléments enfants, seul le premier élément devient le corps du message BizTalk.  
  
-   **Chemin--contenu localisé par le chemin du corps**. Utilise l’expression de chemin d’accès au corps de la **expression de chemin de corps** zone de texte pour créer le corps du message BizTalk. L'expression du chemin du corps est évaluée en fonction de l'élément enfant immédiat de l'élément SOAP **Body** d'un message entrant. Lorsque des messages entrants ont des données binaires, vous pouvez utiliser cette option pour que le corps du message BizTalk inclue uniquement les données binaires sans balise.  
  
 Lorsque le **chemin--contenu localisé par le chemin du corps** option est sélectionnée, le **codage de nœud** propriété peut être configurée pour spécifier le type de codage attendu pour le nœud spécifié par l’expression de chemin de corps dans le **expression de chemin de corps** zone de texte. Si l'expression du chemin du corps correspond à plusieurs éléments, seul le premier élément correspondant est utilisé.  
  
> [!NOTE]
>  Pour le **expression de chemin de corps** propriété, uniquement le XPath expressions appropriées pour le traitement de type avant uniquement de XML sont pris en charge. Pour plus d’informations sur les expressions XPath disponibles pour cette propriété, consultez « La meilleure de tous deux mondes : combinant XPath with the XmlReader » à [http://go.microsoft.com/fwlink/?LinkID=75701](http://go.microsoft.com/fwlink/?LinkID=75701).  
  
 Si le **chemin--contenu localisé par le chemin du corps** option est sélectionnée et la **codage de nœud** est définie sur **chaîne**, les adaptateurs WCF attendent que le nœud correspondant a UTF-8 données de caractères encodés. Si les messages entrants incluent les caractères spéciaux XML des données caractère échappé tel que \< et \>, les adaptateurs WCF rétablissent les données de caractères d’échappement lors de la création du corps du message BizTalk. Par exemple, si le nœud correspondant a échappement des données de type caractère tel que  **&lt;FirstName&gt;CONTOSO&lt;/prénom&gt;**  les adaptateurs WCF créent  **\< FirstName\>CONTOSO\</prénom\>**  corps du message dans BizTalk entrant.  
  
 Si le **chemin--contenu localisé par le chemin du corps** option est sélectionnée et la **codage de nœud** est définie sur **Hex** ou **Base64**, le nœud correspondant peut avoir une valide **au format BinHex** ou **Base64** séquence. Si le nœud correspondant a une séquence non valide, le client WCF reçoit **FaultException**, un message d’erreur est consigné dans le journal des événements sur votre ordinateur BizTalk Server et aucun message n’est suspendu.  
  
 Si le **chemin--contenu localisé par le chemin du corps** option est sélectionnée et la **codage de nœud** est définie sur **XML**, les adaptateurs WCF créent le corps du message BizTalk avec le XML externe du nœud sélectionné par l’expression de chemin d’accès au corps de la **expression de chemin de corps** zone de texte.  
  
 Si le nœud correspondant n’a pas de données encodées en tant que spécifié dans le **codage de nœud** propriété, un corps de message BizTalk entrant vide est créé.  
  
 Par exemple, supposons que les adaptateurs d'envoi WCF reçoivent le message SOAP suivant de clients WCF :  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/OrderRefresh</a:Action>   
    <a:MessageID>urn:uuid:59e74507-66d0-4d50-be70-c3ec248b6f78</a:MessageID>   
    <a:ReplyTo>  
       <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>   
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessServiceBizTalk</a:To>   
  </s:Header>  
  <s:Body>  
    <Order xmlns="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
     <OrderDetail>  
       <CustomerID>CONTOSO</CustomerID>   
       <OrderID>00000000</OrderID>   
     </OrderDetail>  
    </Order>  
  </s:Body>  
</s:Envelope>  
```  
  
 Si vous configurez le **corps du message BizTalk entrant** section comme indiqué dans le tableau suivant, le précédent message SOAP entrant devient le corps du message BizTalk entrant.  
  
|Corps de message BizTalk entrant|Expression du chemin du corps|Codage de nœud|  
|----------------------------------|--------------------------|-------------------|  
|**: Enveloppe \<soap : Envelope\>**|Néant|Néant|  
  
 Si vous configurez le **corps du message BizTalk** section comme indiqué dans le tableau suivant, les adaptateurs WCF créent le corps BizTalk entrant message contienne uniquement les **commande** élément dans la liste précédente messages SOAP entrants.  
  
|Corps de message BizTalk entrant|Expression du chemin du corps|Codage de nœud|  
|----------------------------------|--------------------------|-------------------|  
|**Corps : contenu de \<soap : Body\> élément**|Néant|Néant|  
  
 Si vous configurez le **corps du message BizTalk** section comme indiqué dans le tableau suivant, les adaptateurs WCF attendent que le nœud entrant correspondant de l’expression de chemin de corps aura des données de type caractère encodé UTF-8.  
  
|Corps de message BizTalk entrant|Expression du chemin du corps|Codage de nœud|  
|----------------------------------|--------------------------|-------------------|  
|**Chemin--contenu localisé par le chemin du corps**|/ * [local-name () = 'Order'] /\*[local-name () = 'OrderDetail'] /\*[local-name () = « CustomerID »]|**Chaîne**|  
  
 Pour le précédent message SOAP entrant, les adaptateurs WCF utilisent les données de caractères, **CONTOSO**, de la **CustomerID** élément pour créer le corps du message BizTalk entrant.  
  
> [!NOTE]
>  Vous ne pouvez pas utiliser la syntaxe abrégée de XPath, **/Order/OrderDetail/CustomerID**, pour le précédent message SOAP entrant. Il s’agit, car la syntaxe abrégée de XPath renvoie le nœud non déclaré dans un espace de noms et le **CustomerID** élément dans le précédent message SOAP est déclaré dans le **http:// Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess** espace de noms par des espaces de noms par défaut.  
  
 Si vous configurez le **corps du message BizTalk** section comme indiqué dans le tableau suivant, le **CustomID** élément dans le précédent message SOAP entrant doit avoir une valide **BinHex**ou **Base64** séquence.  
  
|Corps de message BizTalk entrant|Expression du chemin du corps|Codage de nœud|  
|----------------------------------|--------------------------|-------------------|  
|**Chemin--contenu localisé par le chemin du corps**|/ * [local-name () = 'Order'] /\*[local-name () = 'OrderDetail'] /\*[local-name () = « CustomerID »]|**Hex** ou **en Base64**|  
  
 Si vous configurez le **corps du message BizTalk** section comme indiqué dans le tableau suivant, les adaptateurs WCF créent le corps du message BizTalk entrant pour le précédent message SOAP entrant comme indiqué dans le code après le tableau.  
  
|Corps de message BizTalk entrant|Expression du chemin du corps|Codage de nœud|  
|----------------------------------|--------------------------|-------------------|  
|**Chemin--contenu localisé par le chemin du corps**|/ * [local-name () = 'Order'] /\*[local-name () = 'OrderDetail'] /\*[local-name () = « CustomerID »]|**XML**|  
  
```  
<CustomerID xmlns="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">CONTOSO</CustomerID>   
```  
  
## <a name="specifying-the-source-of-the-outbound-wcf-message-body"></a>Spécification de la source du corps du message WCF sortant  
 Vous pouvez contrôler la création du corps du message BizTalk sortant à partir d'un corps de message BizTalk à envoyer par l'intermédiaire d'adaptateurs WCF. Pour spécifier comment le corps du message BizTalk est placé dans le corps du message WCF sortant, vous pouvez utiliser une des options suivantes dans le **le corps du message WCF sortant** section sur le **Messages** onglet comme indiqué dans les chiffres dans la section précédente :  
  
-   **Corps--Corps du message de réponse de BizTalk**. Utilise le corps du message BizTalk pour créer le contenu de SOAP **corps** élément d’un message sortant. Le corps du message BizTalk sortant devient le corps du message SOAP sortant.  
  
-   **Modèle--contenu spécifié par le modèle**. Utilise le modèle fourni dans le **XML** zone de texte pour créer le contenu de SOAP **corps** élément d’un message sortant. Les adaptateurs WCF avec **corps--corps du message de réponse BizTalk** (la valeur par défaut) option n’autorisent pas l’envoi de message non-XML tels que des images bitmap et des données de caractères. Vous pouvez utiliser la **modèle--contenu spécifié par le modèle** option pour les adaptateurs WCF envoyer des messages non XML codés dans **base64**, **hexadécimal**, ou **chaîne** .  
  
 Lorsque le **modèle--contenu spécifié par le modèle** option est sélectionnée, vous devez fournir un élément XML de modèle arbitraire dans le **corps de message WCF sortant - XML** zone de texte. L’élément XML du modèle doit contenir les éléments suivants **bts-msg-body** élément qu’une seule fois et qu’une seule fois, sauf si l’élément XML de modèle est vide :  
  
```  
<bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2010" encoding="[base64|hex|string|xml]"/>  
```  
  
 Les adaptateurs WCF encodent le corps du message BizTalk en fonction de la **codage** d’attribut dans le modèle XML, puis remplacez le **bts-msg-body** élément avec le corps du message BizTalk encodé lors de la création messages WCF sortants. Si le **corps de message WCF sortant - XML** zone de texte est vide, les adaptateurs WCF encodent le corps du message BizTalk dans **Base64**, puis placez le **Base64** de séquence dans le corps du message SOAP sortant.  
  
 Si le **codage** attribut dans le modèle XML est défini sur **chaîne**, les adaptateurs WCF encodent le corps du message BizTalk en tant que données de type caractère encodé UTF-8, dans lequel les XML caractères spéciaux tels que \< et \> sont ignorés.  
  
 Si le **codage** attribut dans le modèle XML est défini sur **base64** ou **hexadécimal**, les adaptateurs WCF encodent le corps du message BizTalk en tant qu’un **BinHex** ou **Base64** séquence.  
  
 Si le **codage** attribut dans le modèle XML est défini sur **xml**, les adaptateurs WCF remplacent le **bts-msg-body** élément avec le corps du message BizTalk sortant pour créer le messages WCF sortants.  
  
 Par exemple, supposons que les adaptateurs WCF doivent envoyer le corps du message BizTalk suivant à des clients WCF :  
  
```  
<ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
  <ns0:OrderDetail>  
    <ns0:CustomerID>CONTOSO</ns0:CustomerID>  
    <ns0:OrderID>01A2c</ns0:OrderID>  
  </ns0:OrderDetail>  
</ns0:Order>  
```  
  
 Si vous configurez le **le corps du message WCF sortant** section comme indiqué dans le tableau suivant, les adaptateurs WCF créent les messages WCF sortants comme indiqué dans le code après le tableau.  
  
|Corps de message WCF sortant|XML|  
|-------------------------------|---------|  
|**Corps : Corps du message de réponse de BizTalk**|Néant|  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/Request</a:Action>  
    <a:MessageID>urn:uuid:6a706a54-c4f5-4767-909d-a992c7c26dba</a:MessageID>  
    <a:ReplyTo>  
<a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessService</a:To>  
  </s:Header>  
  <s:Body>  
    <ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
  <ns0:OrderDetail>  
    <ns0:CustomerID>CONTOSO</ns0:CustomerID>  
    <ns0:OrderID>01A2c</ns0:OrderID>  
  </ns0:OrderDetail>  
</ns0:Order>  
  </s:Body>  
</s:Envelope>  
```  
  
 Si vous configurez le **le corps du message WCF sortant** section comme indiqué dans le tableau suivant, les adaptateurs WCF créent les messages WCF sortants comme indiqué dans le code après le tableau.  
  
|Corps de message WCF sortant|XML|  
|-------------------------------|---------|  
|**Corps : Corps du message de réponse de BizTalk**|\<Livre\><br /><br /> \<**BTS-msg-body** xmlns = « http://www.microsoft.com/schemas/bts2010 » encoding = »**chaîne**« /\><br /><br /> \</ Book\>|  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/Request</a:Action>  
    <a:MessageID>urn:uuid:05dde292-eedd-467e-b0d2-f1b8f0757410</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessService</a:To>  
  </s:Header>  
  <s:Body>  
    <Book><ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  <ns0:OrderDetail>    <ns0:CustomerID>CONTOSO</ns0:CustomerID>    <ns0:OrderID> 01A2c</ns0:OrderID>  </ns0:OrderDetail></ns0:Order>  
    </Book>  
  </s:Body>  
</s:Envelope>  
```  
  
 Si vous configurez le **le corps du message WCF sortant** section comme indiqué dans le tableau suivant, les adaptateurs WCF créent les messages WCF sortants comme indiqué dans le code après le tableau.  
  
|Corps de message WCF sortant|XML|  
|-------------------------------|---------|  
|**Corps : Corps du message de réponse de BizTalk**|\<Livre\><br /><br /> \<**BTS-msg-body** xmlns = « http://www.microsoft.com/schemas/bts2010 » encoding = »**base64**» /\><br /><br /> \</ Book\>|  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://ww  
w.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe  
/OrderProcess/IOrderProcess/Request</a:Action>  
    <a:MessageID>urn:uuid:cb3cac6d-a542-4a90-bad8-cdbfa8251112</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessSer  
vice</a:To>  
  </s:Header>  
  <s:Body>  
    <Book>77u/PG5zMDpPcmRlciB4bWxuczpuczA9Imh0dHA6Ly9NaWNyb3NvZnQuU2FtcGxlcy5CaX  
pUYWxrLk5ldE5hbWVkUGlwZS9PcmRlclByb2Nlc3MiPg0KICA8bnMwOk9yZGVyRGV0YWlsPg0KICAgID  
xuczA6Q3VzdG9tZXJJRD5DT05UT1NPPC9uczA6Q3VzdG9tZXJJRD4NCiAgICA8bnMwOk9yZGVySUQ+MD  
FBMmM8L25zMDpPcmRlcklEPg0KICA8L25zMDpPcmRlckRldGFpbD4NCjwvbnMwOk9yZGVyPg==</Book  
>  
  </s:Body>  
</s:Envelope>  
```  
  
 Si vous configurez le **le corps du message WCF sortant** section comme indiqué dans le tableau suivant, les adaptateurs WCF créent les messages WCF sortants comme indiqué dans le code après le tableau.  
  
|Corps de message WCF sortant|XML|  
|-------------------------------|---------|  
|**Corps : Corps du message de réponse de BizTalk**|\<Livre\><br /><br /> \<**BTS-msg-body** xmlns = « http://www.microsoft.com/schemas/bts2010 » encoding = »**xml**» /\><br /><br /> \</ Book\>|  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/Request</a:A  
ction>  
    <a:MessageID>{513C123C-0600-4A1C-BEE2-EF83E0EFEB15}</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessServiceBizTalk</a:To>  
  </s:Header>  
  <s:Body>  
    <Book>  
      <ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
  <ns0:OrderDetail>  
    <ns0:CustomerID>CustomerID_0</ns0:CustomerID>  
    <ns0:OrderID>OrderID_0</ns0:OrderID>  
  </ns0:OrderDetail>  
</ns0:Order>  
    </Book>  
  </s:Body>  
</s:Envelope>  
```