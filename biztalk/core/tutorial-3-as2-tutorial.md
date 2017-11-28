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
# <a name="tutorial-3-as2-tutorial"></a><span data-ttu-id="54a25-102">Didacticiel 3 : Didacticiel AS2</span><span class="sxs-lookup"><span data-stu-id="54a25-102">Tutorial 3: AS2 Tutorial</span></span>
<span data-ttu-id="54a25-103">Dans ce didacticiel, vous allez configurer une solution qui reçoit et envoie des messages EDIINT/AS2 via un transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="54a25-103">In this tutorial, you set up a solution that receives and sends EDIINT/AS2-encoded messages over an HTTP transport.</span></span>  
  
 <span data-ttu-id="54a25-104">**Fonctionne de la Solution du didacticiel**</span><span class="sxs-lookup"><span data-stu-id="54a25-104">**How the Tutorial Solution Works**</span></span>  
  
 <span data-ttu-id="54a25-105">La solution effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="54a25-105">The solution will do the following:</span></span>  
  
-   <span data-ttu-id="54a25-106">Réception d'un message AS2 à partir d'un partenaire (Fabrikam).</span><span class="sxs-lookup"><span data-stu-id="54a25-106">Receive an AS2 message from a partner (Fabrikam)</span></span>  
  
-   <span data-ttu-id="54a25-107">Renvoi d'une réponse MDN de manière asynchrone au partenaire.</span><span class="sxs-lookup"><span data-stu-id="54a25-107">Return an MDN response asynchronously to the partner</span></span>  
  
-   <span data-ttu-id="54a25-108">Traitement de la charge EDI du message AS2.</span><span class="sxs-lookup"><span data-stu-id="54a25-108">Process the EDI payload of the AS2 message</span></span>  
  
-   <span data-ttu-id="54a25-109">Renvoi d'un accusé de réception 997 au partenaire (Fabrikam) via AS2.</span><span class="sxs-lookup"><span data-stu-id="54a25-109">Return a 997 acknowledgment to the partner (Fabrikam) over AS2</span></span>  
  
-   <span data-ttu-id="54a25-110">Acheminement d'un fichier XML contenant la charge du message EDI vers une application principale de l'organisation d'origine (Contoso).</span><span class="sxs-lookup"><span data-stu-id="54a25-110">Route an XML file containing the payload of the EDI message to a backend application of the home organization (Contoso).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="54a25-111">Cette solution n'utilise pas les méthodes de signature ou de chiffrement pour assurer la sécurité des messages AS2.</span><span class="sxs-lookup"><span data-stu-id="54a25-111">This solution does not use signing or encryption to help ensure the security of AS2 messages.</span></span>  
  
 <span data-ttu-id="54a25-112">**Composants du didacticiel**</span><span class="sxs-lookup"><span data-stu-id="54a25-112">**Tutorial Components**</span></span>  
  
 <span data-ttu-id="54a25-113">La solution utilisera les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="54a25-113">This solution will use the following:</span></span>  
  
-   <span data-ttu-id="54a25-114">Un BTS Http filtre ISAPI de réception pour recevoir le message AS2/EDI à partir de l’expéditeur **(/Contoso/BTSHTTPReceive.dll**).</span><span class="sxs-lookup"><span data-stu-id="54a25-114">A BTS Http Receive ISAPI Filter to receive the AS2/EDI message from the sender **(/Contoso/BTSHTTPReceive.dll**).</span></span>  
  
-   <span data-ttu-id="54a25-115">Une page Web ASPX pour simuler le partenaire en renvoyant un accusé de réception 997 ainsi qu’un MDN (**http://localhost/Fabrikam/Default.aspx**).</span><span class="sxs-lookup"><span data-stu-id="54a25-115">An ASPX Web page to simulate the partner by returning a 997 acknowledgment and an MDN (**http://localhost/Fabrikam/Default.aspx**).</span></span>  
  
-   <span data-ttu-id="54a25-116">Un fichier de projet que vous utiliserez pour déployer un schéma 864 et autres schémas (**Schemas.btproj**).</span><span class="sxs-lookup"><span data-stu-id="54a25-116">A project file that you will use to deploy an 864 schema and other schemas (**Schemas.btproj**).</span></span>  
  
-   <span data-ttu-id="54a25-117">Un HTTP unidirectionnel emplacement de réception pour recevoir le fichier EDI (**Receive_AS2**).</span><span class="sxs-lookup"><span data-stu-id="54a25-117">A one-way HTTP receive location to receive the EDI file (**Receive_AS2**).</span></span> <span data-ttu-id="54a25-118">Cet emplacement de réception utilise le pipeline AS2EdiReceive par défaut contenant le décodeur AS2 et le désassembleur EDI.</span><span class="sxs-lookup"><span data-stu-id="54a25-118">This receive location uses the default AS2EdiReceive pipeline that contains the AS2 Decoder and EDI Disassembler.</span></span>  
  
-   <span data-ttu-id="54a25-119">Un HTTP dynamique port d’envoi pour renvoyer un MDN asynchrone (**Send_Async_MDN**).</span><span class="sxs-lookup"><span data-stu-id="54a25-119">A dynamic HTTP send port to return an asynchronous MDN (**Send_Async_MDN**).</span></span> <span data-ttu-id="54a25-120">Ce port d'envoi utilise le pipeline AS2Send contenant l'encodeur AS2.</span><span class="sxs-lookup"><span data-stu-id="54a25-120">This send port uses the AS2Send pipeline that contains the AS2 Encoder.</span></span>  
  
-   <span data-ttu-id="54a25-121">Un fichier unidirectionnel statique port d’envoi pour router la charge EDI dans un fichier XML dans un dossier principal (**Send_Payload_EdiXml**).</span><span class="sxs-lookup"><span data-stu-id="54a25-121">A static one-way FILE send port to route the EDI payload in an XML file to a back-end folder (**Send_Payload_EdiXml**).</span></span> <span data-ttu-id="54a25-122">Ce port d'envoi utilise le pipeline d'envoi PassThruTransmit.</span><span class="sxs-lookup"><span data-stu-id="54a25-122">This send port uses the PassThruTransmit send pipeline.</span></span>  
  
-   <span data-ttu-id="54a25-123">Un HTTP unidirectionnel statique port d’envoi pour renvoyer un accusé de réception 997 au partenaire via AS2 (**Send_Async_997**).</span><span class="sxs-lookup"><span data-stu-id="54a25-123">A static one-way HTTP send port to return a 997 acknowledgment to the partner over AS2 (**Send_Async_997**).</span></span> <span data-ttu-id="54a25-124">Ce port d'envoi utilise le pipeline AS2Send incluant l'encodeur AS2, mais n'a pas besoin de l'assembleur EDI.</span><span class="sxs-lookup"><span data-stu-id="54a25-124">This send port uses the AS2Send pipeline that includes the AS2 Encoder, but has no need for the EDI Assembler.</span></span>  
  
-   <span data-ttu-id="54a25-125">Un fichier de projet que vous allez utiliser pour générer une application pour envoyer le fichier EDI du partenaire Fabrikam vers BizTalk (**Sender.csproj**).</span><span class="sxs-lookup"><span data-stu-id="54a25-125">A project file that you will use to build an application to send the EDI file from the Fabrikam partner to BizTalk (**Sender.csproj**).</span></span>  
  
 <span data-ttu-id="54a25-126">**Flux de messages**</span><span class="sxs-lookup"><span data-stu-id="54a25-126">**Message Flow**</span></span>  
  
 <span data-ttu-id="54a25-127">Le flux de messages de la solution terminée ressemblera au schéma suivant :</span><span class="sxs-lookup"><span data-stu-id="54a25-127">The message flow in the completed solution will be as shown in the following figure:</span></span>  
  
 <span data-ttu-id="54a25-128">![Flux de messages du didacticiel AS2](../core/media/31710c1d-4070-433e-953d-dcbfd0bb07a0.gif "31710c1d-4070-433e-953d-dcbfd0bb07a0")</span><span class="sxs-lookup"><span data-stu-id="54a25-128">![AS2 tutorial message flow](../core/media/31710c1d-4070-433e-953d-dcbfd0bb07a0.gif "31710c1d-4070-433e-953d-dcbfd0bb07a0")</span></span>  
  
 <span data-ttu-id="54a25-129">Les composants de ce didacticiel traitent le message comme suit :</span><span class="sxs-lookup"><span data-stu-id="54a25-129">The tutorial components process the message as follows:</span></span>  
  
1.  <span data-ttu-id="54a25-130">Vous utilisez la **application sender.exe** pour envoyer le message EDI/AS2 d’origine du partenaire Fabrikam à l’ordinateur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="54a25-130">You use the **sender.exe application** to send the original EDI/AS2 message from the partner Fabrikam to the BizTalk Server computer.</span></span> <span data-ttu-id="54a25-131">Sender.exe envoie le message EDI/AS2 vers le répertoire virtuel Contoso.</span><span class="sxs-lookup"><span data-stu-id="54a25-131">Sender.exe sends the EDI/AS2 message to the Contoso virtual directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="54a25-132">Les événements dans cette liste peuvent se produire dans un ordre différent de celui indiqué.</span><span class="sxs-lookup"><span data-stu-id="54a25-132">The events in this list may not occur in the order shown.</span></span>  
    >   
    >  <span data-ttu-id="54a25-133">Le message de test est X12_00401_864.edi dans \Program Files\Microsoft BizTalk Server 20xx\SDK\AS2 Tutorial.</span><span class="sxs-lookup"><span data-stu-id="54a25-133">The test message is X12_00401_864.edi in \Program Files\Microsoft BizTalk Server 20xx\SDK\AS2 Tutorial.</span></span>  
  
2.  <span data-ttu-id="54a25-134">Le **Receive_AS2** unidirectionnel de réception emplacement reçoit le message EDI de Fabrikam, à l’aide de l’extension ISAPI BTSHTTPReceive.dll pour récupérer le fichier à partir du répertoire virtuel Contoso.</span><span class="sxs-lookup"><span data-stu-id="54a25-134">The **Receive_AS2** one-way receive location receives the EDI message from Fabrikam, using the BTSHTTPReceive.dll ISAPI extension to pick the file up from the Contoso virtual directory.</span></span> <span data-ttu-id="54a25-135">Le pipeline de réception décode le message AS2, désassemble l'échange EDI, puis dépose le message XML dans la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="54a25-135">The receive pipeline decodes the AS2 message, disassembles the EDI interchange, and then drops the message XML into the MessageBox.</span></span>  
  
3.  <span data-ttu-id="54a25-136">Le pipeline de réception génère un MDN pour le message AS2, et le MDN étant configuré pour être asynchrone, il dépose celui-ci dans la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="54a25-136">The receive pipeline generates an MDN for the AS2 message, and since the MDN is set up to be asynchronous, the receive pipeline drops the MDN into the MessageBox.</span></span>  
  
4.  <span data-ttu-id="54a25-137">Le pipeline de réception génère un accusé de réception 997 en réponse à l'échange EDI, et dépose le 997 dans la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="54a25-137">The receive pipeline generates a 997 acknowledgment in response to the EDI interchange, and drops the 997 into the MessageBox.</span></span>  
  
5.  <span data-ttu-id="54a25-138">Le **Send_Payload_EdiXml** port d’envoi unidirectionnel statique récupère la charge EDI dans la MessageBox, le filtrage sur le BTS. Propriété de contexte de MessageType.</span><span class="sxs-lookup"><span data-stu-id="54a25-138">The **Send_Payload_EdiXml** static one-way send port picks up the EDI payload from the MessageBox, filtering on the BTS.MessageType context property.</span></span>  
  
6.  <span data-ttu-id="54a25-139">La charge utile de port d’envoi envoie le fichier XML contenant la charge EDI vers l’application Contoso principale, représentée par le \\_EDIXMLToContoso dossier.</span><span class="sxs-lookup"><span data-stu-id="54a25-139">The payload send port sends the XML file containing the EDI payload to the back-end Contoso application, represented by the \\_EDIXMLToContoso folder.</span></span> <span data-ttu-id="54a25-140">Ce port d'envoi utilise un pipeline d'envoi PassThruTransmit.</span><span class="sxs-lookup"><span data-stu-id="54a25-140">This send port uses a PassThruTransmit send pipeline.</span></span>  
  
7.  <span data-ttu-id="54a25-141">Le **Send_Async_MDN** port d’envoi dynamique récupère le MDN asynchrone dans la MessageBox, le filtrage sur la propriété de contexte EdiIntAS.IsAS2AsynchronousMdn.</span><span class="sxs-lookup"><span data-stu-id="54a25-141">The **Send_Async_MDN** dynamic send port picks up the asynchronous MDN from the MessageBox, filtering on the EdiIntAS.IsAS2AsynchronousMdn context property.</span></span>  
  
8.  <span data-ttu-id="54a25-142">Le MDN envoyer port renvoie le MDN le \\dossier _MDNToFabrikam.</span><span class="sxs-lookup"><span data-stu-id="54a25-142">The MDN send port returns the MDN to the \\_MDNToFabrikam folder.</span></span> <span data-ttu-id="54a25-143">Dans la mesure où il s’agit d’un port d’envoi dynamique, il utilisera l’adresse dans la ligne Receipt-Delivery-Option dans l’en-tête du message (**http://localhost/Fabrikam/Default.aspx? Destination = _MDNToFabrikam**) pour router le message vers le \\dossier _MDNToFabrikam.</span><span class="sxs-lookup"><span data-stu-id="54a25-143">Since this is a dynamic send port, it will use the address in the Receipt-Delivery-Option line in the header of the message (**http://localhost/Fabrikam/Default.aspx?Destination=_MDNToFabrikam**) to route the message to the \\_MDNToFabrikam folder.</span></span>  
  
9. <span data-ttu-id="54a25-144">Le **Send_Async_997** port récupère le 997 dans la MessageBox, le filtrage sur l’envoi d’envoi. Propriété de contexte de MessageType.</span><span class="sxs-lookup"><span data-stu-id="54a25-144">The **Send_Async_997** send port picks up the 997 from the MessageBox, filtering on the BTS.MessageType context property.</span></span>  
  
10. <span data-ttu-id="54a25-145">Le 997 port d’envoi utilise de transport HTTP pour envoyer le message 997 généré par le EdiReceive du pipeline de réception le \\_997ToFabrikam dossier.</span><span class="sxs-lookup"><span data-stu-id="54a25-145">The 997 send port uses HTTP transport to send the 997 message generated by the EdiReceive receive pipeline to the \\_997ToFabrikam folder.</span></span> <span data-ttu-id="54a25-146">Le port d’envoi envoie le message à la page default.aspx de Fabrikam, à l’aide de l’URI **http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam**.</span><span class="sxs-lookup"><span data-stu-id="54a25-146">The send port sends the message to the Fabrikam default.aspx page, using the URI **http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam**.</span></span> <span data-ttu-id="54a25-147">La page default.aspx envoie ensuite le 997 vers le \\_997ToFabrikam dossier.</span><span class="sxs-lookup"><span data-stu-id="54a25-147">The default.aspx page then sends the 997 to the \\_997ToFabrikam folder.</span></span>  
  
 <span data-ttu-id="54a25-148">Pour pouvoir suivre ce didacticiel, vous devez être familiarisé avec les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="54a25-148">To do this tutorial, you should be knowledgeable about the following:</span></span>  
  
-   <span data-ttu-id="54a25-149">pipelines BizTalk Server et les composants associés ;</span><span class="sxs-lookup"><span data-stu-id="54a25-149">BizTalk Server pipelines and pipeline components</span></span>  
  
-   <span data-ttu-id="54a25-150">Adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="54a25-150">HTTP Adapter</span></span>  
  
-   <span data-ttu-id="54a25-151">ports et emplacements de réception ;</span><span class="sxs-lookup"><span data-stu-id="54a25-151">Receive ports and locations</span></span>  
  
-   <span data-ttu-id="54a25-152">Ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="54a25-152">Send ports</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="54a25-153">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="54a25-153">In This Section</span></span>  
  
-   [<span data-ttu-id="54a25-154">Étape 1 : Préparer le didacticiel AS2</span><span class="sxs-lookup"><span data-stu-id="54a25-154">Step 1: Prepare for the AS2 Tutorial</span></span>](../core/step-1-prepare-for-the-as2-tutorial.md)  
  
-   [<span data-ttu-id="54a25-155">Étape 2 : Créer et déployer l’exemple X12 schéma</span><span class="sxs-lookup"><span data-stu-id="54a25-155">Step 2: Create and Deploy the Sample X12 Schema</span></span>](../core/step-2-create-and-deploy-the-sample-x12-schema.md)  
  
-   [<span data-ttu-id="54a25-156">Étape 3 : Configurer un tiers et un profil d’entreprise pour votre organisation</span><span class="sxs-lookup"><span data-stu-id="54a25-156">Step 3: Configure a Party and Business Profile for Your Organization</span></span>](../core/step-3-configure-a-party-and-business-profile-for-your-organization2.md)  
  
-   [<span data-ttu-id="54a25-157">Étape 4 : Configurer un tiers et un profil d’entreprise pour votre partenaire commercial</span><span class="sxs-lookup"><span data-stu-id="54a25-157">Step 4: Configure a Party and Business Profile for Your Trading Partner</span></span>](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner2.md)  
  
-   [<span data-ttu-id="54a25-158">Étape 5 : Configurer les Pages Web du partenaire commercial</span><span class="sxs-lookup"><span data-stu-id="54a25-158">Step 5: Configure the Trading Partner Web Pages</span></span>](../core/step-5-configure-the-trading-partner-web-pages.md)  
  
-   [<span data-ttu-id="54a25-159">Étape 6 : Configurer EDI-AS2 emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="54a25-159">Step 6: Configure the EDI-AS2 Receive Location</span></span>](../core/step-6-configure-the-edi-as2-receive-location.md)  
  
-   [<span data-ttu-id="54a25-160">Étape 7 : Configurer le Port d’envoi MDN</span><span class="sxs-lookup"><span data-stu-id="54a25-160">Step 7: Configure the MDN Send Port</span></span>](../core/step-7-configure-the-mdn-send-port.md)  
  
-   [<span data-ttu-id="54a25-161">Étape 8 : Configurer le Port de 997 envoi</span><span class="sxs-lookup"><span data-stu-id="54a25-161">Step 8: Configure the 997 Send Port</span></span>](../core/step-8-configure-the-997-send-port.md)  
  
-   [<span data-ttu-id="54a25-162">Étape 9 : Configurer le Port d’envoi EDI charge utile</span><span class="sxs-lookup"><span data-stu-id="54a25-162">Step 9: Configure the EDI Payload Send Port</span></span>](../core/step-9-configure-the-edi-payload-send-port.md)  
  
-   [<span data-ttu-id="54a25-163">Étape 10 : Configurer l’accord de partenariat X12 et AS2 commerciaux</span><span class="sxs-lookup"><span data-stu-id="54a25-163">Step 10: Configure the X12 and AS2 Trading Partner Agreement</span></span>](../core/step-10-configure-the-x12-and-as2-trading-partner-agreement.md)  
  
-   [<span data-ttu-id="54a25-164">Étape 11 : Tester la Solution AS2</span><span class="sxs-lookup"><span data-stu-id="54a25-164">Step 11: Test the AS2 Solution</span></span>](../core/step-11-test-the-as2-solution.md)  
  
## <a name="see-also"></a><span data-ttu-id="54a25-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54a25-165">See Also</span></span>  
 [<span data-ttu-id="54a25-166">Didacticiels de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="54a25-166">BizTalk Server Tutorials</span></span>](../core/biztalk-server-tutorials.md)