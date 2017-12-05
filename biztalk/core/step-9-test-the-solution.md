---
title: "Étape 9 : Tester la Solution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df446ccc-add3-4dd3-b674-253dda385541
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89a3722d6d8e1d4b730341dfaf16d60af1686f21
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-9-test-the-solution"></a>Étape 9 : Tester la Solution
Cette rubrique vous invite à tester l’application hybride via l’envoi d’un message de commande client X12 840 vers le point de terminaison HTTP où est déployé l’accord EDI. L’exemple de message de commande client ressemble à ce qui suit :  
  
```  
ISA*00*          *00*          *ZZ*CONTOSO        *ZZ*NORTHWIND      *991221*1226*U*00401*000000025*0*T*:~  
GS*PO*THEM*US*19991221*1226*1*X*004010~  
ST*840*0002~  
BQT*00*BQT02*20120619*001*20120719~  
PER*1A*John*EM*John@contoso.com~  
N1*001~  
N2*co~  
N3*Contoso*One Contoso Way~  
N4*Redmond*WA*98052*US~  
PO1*PO101*121*01*10*AA*A1*1~  
CTT*475~  
SE*10*0002~  
GE*1*1~  
IEA*1*000000025~  
```  
  
 Dans ce message, le segment en surbrillance (ligne commençant par **PO1**) contient la quantité commandée. La quantité commandée dans ce message est *121*. Par conséquent, si vous envoyez ce message, il doit être inséré dans le **SalesOrder** table. Vous pouvez définir la quantité sur une valeur inférieure à 100 et renvoyer le message. Celui-ci doit ensuite être envoyé à l’emplacement de fichier que vous avez spécifié dans le port d’envoi FILE.  
  
 Pour envoyer ce message à l’accord EDI, vous pouvez utiliser la **MessageSender** outil fourni avec les exemples de [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]. Vous pouvez télécharger les exemples à partir de [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057).  
  
### <a name="to-send-a-message"></a>Pour envoyer un message  
  
1.  Recherchez le **MessageSender** dans l’exemple de package de projet et générez-le.  
  
2.  Utilisez résultant **MessageSender** exécutable de ligne de commande (sous le dossier \bin\Debug du projet) pour envoyer des messages à l’accord EDI déployé. Cet outil accepte le paramètre de ligne de commande au format suivant :  
  
    ```  
    MessageSender.exe <ServiceBusNamespace> <IssuerName> <IssuerKey> <EDI agreement endpoint> <MessageFilepath> <ContentType>  
    ```  
  
     WHERE,  
  
    |Nom du paramètre| Description|  
    |--------------------|-----------------|  
    |ServiceBusNamespace|Espace de noms du Service Bus|  
    |IssuerName|Nom de l’émetteur pour l’espace de noms spécifié|  
    |IssuerKey|Clé de l’émetteur pour l’espace de noms spécifié|  
    |Point de terminaison de l’accord EDI|Point de terminaison où est déployé l’accord EDI. Vous pouvez obtenir cette URL de point de terminaison à partir de l’onglet Paramètres de réception (et dans laquelle la page Transport) de l’accord EDI que vous avez déployé dans [étape 2 (pour Azure) : création d’un accord EDI](../core/step-2-for-azure-create-an-edi-agreement.md).|  
    |MessageFilePath|Chemin d’accès au fichier contenant l’exemple de message de requête.|  
    |ContentType|Pour ce didacticiel, définissez ce paramètre sur **texte/brut**.|  
  
     Ouvrez une invite de commandes et accédez à la solution dans laquelle vous avez créé le **MessageSender** projet. Exécutez la commande suivante pour envoyer le message de requête avec une quantité commandée inférieure à 100 :  
  
    ```  
    MessageSender.exe <service bus namespace> owner <issuer key>https://<namespace>.servicebus.appfabriclabs.com/7576ff3d-a0f3-4a46-a4f6-f5be4a50616a/DemoAgreement<path to the sample message> "text/plain"  
    ```  
  
3.  Ouvrez SQL Server Management Studio, connectez-vous à la base de données qui contient le **SalesOrder** de table et vérifiez qu’un nouvel enregistrement est inséré dans la table. Notez la valeur dans la **Qty** colonne ; il doit être *121*.  
  
4.  Utilisez **MessageSender** pour envoyer un autre message, mais cette fois la valeur de la quantité commandée dans le message à *99*. Vous remarquerez qu’à présent aucun enregistrement n’est inséré dans le **SalesOrder** table. Au lieu de cela, le message est copié vers l’emplacement de fichier spécifié pour la réception des messages par quantité commandée inférieure à 100. Le message reçu ressemble à ceci :  
  
    ```  
    <ns1:SalesOrder xmlns:ns0="http://schemas.microsoft.com/BizTalk/EDI/X12/2006" xmlns:ns1="http://ECommerceSalesOrder.Inbound">  
      <CompanyCode>co</CompanyCode>  
      <PartID>1</PartID>  
      <Quantity>99</Quantity>  
      <AskPrice>10</AskPrice>  
      <RequestShipmentDate>2012-07-19</RequestShipmentDate>  
      <Address>  
        <Line1>Contoso</Line1>  
        <Line2>One Contoso Way</Line2>  
        <City>Redmond</City>  
        <State>WA</State>  
        <Country>US</Country>  
        <Zipcode>98052</Zipcode>  
      </Address>  
      <Contact>  
        <Firstname>John</Firstname>  
        <Lastname>John@contoso.com</Lastname>  
      </Contact>  
      <Comments>Order from Partnerco</Comments>  
      <DateNow>2012-06-19</DateNow>  
    </ns1:SalesOrder>  
  
    ```  
  
     Notez la valeur dans la **quantité** élément. Il s’agit de *99*.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)