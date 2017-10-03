---
title: "Didacticiel 3 : AS2 didacticiel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 018829a9-e670-4b87-bac5-7f7b1332d90e
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03de45aa09b2704f205b81db4c513a0da5770ee3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-3-as2-tutorial"></a>Didacticiel 3 : Didacticiel AS2
Dans ce didacticiel, vous allez configurer une solution qui reçoit et envoie des messages EDIINT/AS2 via un transport HTTP.  
  
 **Fonctionne de la Solution du didacticiel**  
  
 La solution effectue les opérations suivantes :  
  
-   Réception d'un message AS2 à partir d'un partenaire (Fabrikam).  
  
-   Renvoi d'une réponse MDN de manière asynchrone au partenaire.  
  
-   Traitement de la charge EDI du message AS2.  
  
-   Renvoi d'un accusé de réception 997 au partenaire (Fabrikam) via AS2.  
  
-   Acheminement d'un fichier XML contenant la charge du message EDI vers une application principale de l'organisation d'origine (Contoso).  
  
    > [!NOTE]
    >  Cette solution n'utilise pas les méthodes de signature ou de chiffrement pour assurer la sécurité des messages AS2.  
  
 **Composants du didacticiel**  
  
 La solution utilisera les éléments suivants :  
  
-   Un BTS Http filtre ISAPI de réception pour recevoir le message AS2/EDI à partir de l’expéditeur **(/Contoso/BTSHTTPReceive.dll**).  
  
-   Une page Web ASPX pour simuler le partenaire en renvoyant un accusé de réception 997 ainsi qu’un MDN (**http://localhost/Fabrikam/Default.aspx**).  
  
-   Un fichier de projet que vous utiliserez pour déployer un schéma 864 et autres schémas (**Schemas.btproj**).  
  
-   Un HTTP unidirectionnel emplacement de réception pour recevoir le fichier EDI (**Receive_AS2**). Cet emplacement de réception utilise le pipeline AS2EdiReceive par défaut contenant le décodeur AS2 et le désassembleur EDI.  
  
-   Un HTTP dynamique port d’envoi pour renvoyer un MDN asynchrone (**Send_Async_MDN**). Ce port d'envoi utilise le pipeline AS2Send contenant l'encodeur AS2.  
  
-   Un fichier unidirectionnel statique port d’envoi pour router la charge EDI dans un fichier XML dans un dossier principal (**Send_Payload_EdiXml**). Ce port d'envoi utilise le pipeline d'envoi PassThruTransmit.  
  
-   Un HTTP unidirectionnel statique port d’envoi pour renvoyer un accusé de réception 997 au partenaire via AS2 (**Send_Async_997**). Ce port d'envoi utilise le pipeline AS2Send incluant l'encodeur AS2, mais n'a pas besoin de l'assembleur EDI.  
  
-   Un fichier de projet que vous allez utiliser pour générer une application pour envoyer le fichier EDI du partenaire Fabrikam vers BizTalk (**Sender.csproj**).  
  
 **Flux de messages**  
  
 Le flux de messages de la solution terminée ressemblera au schéma suivant :  
  
 ![Flux de messages du didacticiel AS2](../core/media/31710c1d-4070-433e-953d-dcbfd0bb07a0.gif "31710c1d-4070-433e-953d-dcbfd0bb07a0")  
  
 Les composants de ce didacticiel traitent le message comme suit :  
  
1.  Vous utilisez la **application sender.exe** pour envoyer le message EDI/AS2 d’origine du partenaire Fabrikam à l’ordinateur BizTalk Server. Sender.exe envoie le message EDI/AS2 vers le répertoire virtuel Contoso.  
  
    > [!NOTE]
    >  Les événements dans cette liste peuvent se produire dans un ordre différent de celui indiqué.  
    >   
    >  Le message de test est X12_00401_864.edi dans \Program Files\Microsoft BizTalk Server 20xx\SDK\AS2 Tutorial.  
  
2.  Le **Receive_AS2** unidirectionnel de réception emplacement reçoit le message EDI de Fabrikam, à l’aide de l’extension ISAPI BTSHTTPReceive.dll pour récupérer le fichier à partir du répertoire virtuel Contoso. Le pipeline de réception décode le message AS2, désassemble l'échange EDI, puis dépose le message XML dans la MessageBox.  
  
3.  Le pipeline de réception génère un MDN pour le message AS2, et le MDN étant configuré pour être asynchrone, il dépose celui-ci dans la MessageBox.  
  
4.  Le pipeline de réception génère un accusé de réception 997 en réponse à l'échange EDI, et dépose le 997 dans la MessageBox.  
  
5.  Le **Send_Payload_EdiXml** port d’envoi unidirectionnel statique récupère la charge EDI dans la MessageBox, le filtrage sur le BTS. Propriété de contexte de MessageType.  
  
6.  La charge utile de port d’envoi envoie le fichier XML contenant la charge EDI vers l’application Contoso principale, représentée par le \\_EDIXMLToContoso dossier. Ce port d'envoi utilise un pipeline d'envoi PassThruTransmit.  
  
7.  Le **Send_Async_MDN** port d’envoi dynamique récupère le MDN asynchrone dans la MessageBox, le filtrage sur la propriété de contexte EdiIntAS.IsAS2AsynchronousMdn.  
  
8.  Le MDN envoyer port renvoie le MDN le \\dossier _MDNToFabrikam. Dans la mesure où il s’agit d’un port d’envoi dynamique, il utilisera l’adresse dans la ligne Receipt-Delivery-Option dans l’en-tête du message (**http://localhost/Fabrikam/Default.aspx? Destination = _MDNToFabrikam**) pour router le message vers le \\dossier _MDNToFabrikam.  
  
9. Le **Send_Async_997** port récupère le 997 dans la MessageBox, le filtrage sur l’envoi d’envoi. Propriété de contexte de MessageType.  
  
10. Le 997 port d’envoi utilise de transport HTTP pour envoyer le message 997 généré par le EdiReceive du pipeline de réception le \\_997ToFabrikam dossier. Le port d’envoi envoie le message à la page default.aspx de Fabrikam, à l’aide de l’URI **http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam**. La page default.aspx envoie ensuite le 997 vers le \\_997ToFabrikam dossier.  
  
 Pour pouvoir suivre ce didacticiel, vous devez être familiarisé avec les éléments suivants :  
  
-   pipelines BizTalk Server et les composants associés ;  
  
-   Adaptateur HTTP  
  
-   ports et emplacements de réception ;  
  
-   Ports d’envoi  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Préparer le didacticiel AS2](../core/step-1-prepare-for-the-as2-tutorial.md)  
  
-   [Étape 2 : Créer et déployer l’exemple X12 schéma](../core/step-2-create-and-deploy-the-sample-x12-schema.md)  
  
-   [Étape 3 : Configurer un tiers et un profil d’entreprise pour votre organisation](../core/step-3-configure-a-party-and-business-profile-for-your-organization2.md)  
  
-   [Étape 4 : Configurer un tiers et un profil d’entreprise pour votre partenaire commercial](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner2.md)  
  
-   [Étape 5 : Configurer les Pages Web du partenaire commercial](../core/step-5-configure-the-trading-partner-web-pages.md)  
  
-   [Étape 6 : Configurer EDI-AS2 emplacement de réception](../core/step-6-configure-the-edi-as2-receive-location.md)  
  
-   [Étape 7 : Configurer le Port d’envoi MDN](../core/step-7-configure-the-mdn-send-port.md)  
  
-   [Étape 8 : Configurer le Port de 997 envoi](../core/step-8-configure-the-997-send-port.md)  
  
-   [Étape 9 : Configurer le Port d’envoi EDI charge utile](../core/step-9-configure-the-edi-payload-send-port.md)  
  
-   [Étape 10 : Configurer l’accord de partenariat X12 et AS2 commerciaux](../core/step-10-configure-the-x12-and-as2-trading-partner-agreement.md)  
  
-   [Étape 11 : Tester la Solution AS2](../core/step-11-test-the-as2-solution.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels de BizTalk Server](../core/biztalk-server-tutorials.md)