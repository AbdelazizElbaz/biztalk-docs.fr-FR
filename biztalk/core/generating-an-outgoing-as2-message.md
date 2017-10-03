---
title: "Génération d’un Message AS2 sortant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 288c8101-9a96-4f98-ae18-df43c7cdb3a0
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90a0b1e37e96086de7d8901b61afa8dea859a388
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generating-an-outgoing-as2-message"></a><span data-ttu-id="197a9-102">Génération d'un message AS2 sortant</span><span class="sxs-lookup"><span data-stu-id="197a9-102">Generating an Outgoing AS2 Message</span></span>
<span data-ttu-id="197a9-103">Les pipelines d'envoi AS2EDISend et AS2Send génèrent un message sortant comme suit.</span><span class="sxs-lookup"><span data-stu-id="197a9-103">The AS2EDISend and AS2Send send pipelines generate an outbound message as follows.</span></span> <span data-ttu-id="197a9-104">Chaque pipeline utilise les propriétés dans l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue pour générer le message AS2 sortant.</span><span class="sxs-lookup"><span data-stu-id="197a9-104">Each pipeline uses the properties in the one-way agreement tab of the **Agreement Properties** dialog box to generate the outgoing AS2 message.</span></span>  
  
## <a name="agreement-destination-and-messageid-determination"></a><span data-ttu-id="197a9-105">Accord, Destination et Détermination de l'ID du message</span><span class="sxs-lookup"><span data-stu-id="197a9-105">Agreement, Destination, and MessageID Determination</span></span>  
 <span data-ttu-id="197a9-106">Les pipelines d'envoi AS2 déterminent l'accord et la destination à utiliser lors de l'envoi d'un message AS2 comme suit :</span><span class="sxs-lookup"><span data-stu-id="197a9-106">The AS2 send pipelines determine the agreement and destination to be used in sending an AS2 message as follows:</span></span>  
  
-   <span data-ttu-id="197a9-107">Pour déterminer l'accord à utiliser lors du traitement d'un message sortant, l'encodeur AS2 tente de faire correspondre les propriétés AS2-To dans le message et l'AS2Identity d'un profil d'entreprise tiers ou le port d'envoi s'abonnant au message et un port d'envoi associé à l'accord.</span><span class="sxs-lookup"><span data-stu-id="197a9-107">To determine the agreement to use in processing an outgoing message, the AS2 encoder attempts to match the AS2-To properties in the message and the AS2Identity for a party’s business profile, or the send port subscribing to the message with a send port associated with the agreement.</span></span> <span data-ttu-id="197a9-108">Pour plus d’informations sur ce processus, consultez [résolution de l’accord pour les Messages AS2 sortants](../core/agreement-resolution-for-outgoing-as2-messages.md).</span><span class="sxs-lookup"><span data-stu-id="197a9-108">For more information on this process, see [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md).</span></span>  
  
-   <span data-ttu-id="197a9-109">Pour déterminer la destination du message, le pipeline d'envoi d'un port d'envoi dynamique utilise la propriété OutboundTransportLocation, qui doit être écrite ou promue dans le contexte par une application principale pour que le port d'envoi dynamique fonctionne.</span><span class="sxs-lookup"><span data-stu-id="197a9-109">To determine the destination of the message, the send pipeline in a dynamic send port uses the OutboundTransportLocation property, which must be written or promoted to the context by a backend application for the dynamic send port to work.</span></span> <span data-ttu-id="197a9-110">Le pipeline d'envoi dans un pipeline d'envoi statique détermine la destination à partir de la propriété AS2-From des propriétés de l'accord AS2 et des identités des propriétés du profil d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="197a9-110">The send pipeline in a static send pipeline will determine the destination from the AS2-From property in the AS2 agreement properties and the identities of the business profile properties.</span></span>  
  
-   <span data-ttu-id="197a9-111">L'encodeur AS2 doit définir l'en-tête MessageId d'un message AS2 sortant.</span><span class="sxs-lookup"><span data-stu-id="197a9-111">The AS2 Encoder needs to set the MessageId header of an outgoing AS2 message.</span></span> <span data-ttu-id="197a9-112">Le pipeline d'envoi détermine le MessageId à partir de la propriété de contexte `EdiIntAS.MessageId` ou `HTTP.UserHttpHeaders`.</span><span class="sxs-lookup"><span data-stu-id="197a9-112">The send pipeline determines the MessageId from either the `EdiIntAS.MessageId` context property or the `HTTP.UserHttpHeaders` context property.</span></span> <span data-ttu-id="197a9-113">Si ces deux propriétés de contexte sont définies, l'encodeur utilise la valeur à partir de la propriété de contexte `HTTP.UserHttpHeaders`.</span><span class="sxs-lookup"><span data-stu-id="197a9-113">If both of those context properties are set, the encoder uses the value from the `HTTP.UserHttpHeaders` context property.</span></span> <span data-ttu-id="197a9-114">Si aucune n'est définie, le pipeline d'envoi génère automatiquement une valeur pour MessageID.</span><span class="sxs-lookup"><span data-stu-id="197a9-114">If neither of them is set, the send pipeline autogenerates a value for MessageID.</span></span>  
  
## <a name="outgoing-message-processing"></a><span data-ttu-id="197a9-115">Traitement des messages sortants</span><span class="sxs-lookup"><span data-stu-id="197a9-115">Outgoing Message Processing</span></span>  
 <span data-ttu-id="197a9-116">Les pipelines d'envoi AS2 effectuent le traitement suivant pour le message AS2 sortant :</span><span class="sxs-lookup"><span data-stu-id="197a9-116">The steps that the AS2 send pipelines use in processing an outgoing AS2 message are as follows:</span></span>  
  
-   <span data-ttu-id="197a9-117">Effectue une copie du message au format natif et la stocke dans la base de données de non-répudiation, si la non-répudiation des messages AS2 est activée dans les propriétés de l'accord.</span><span class="sxs-lookup"><span data-stu-id="197a9-117">Makes a copy of the message in native format, and stores the copy in the non-repudiation database, if non-repudiation of AS2 messages is enabled in agreement properties.</span></span>  
  
-   <span data-ttu-id="197a9-118">L'encodeur AS2 crée les en-têtes HTTP (et AS2) dans la propriété de contexte `HTTP.UserHttpHeaders`.</span><span class="sxs-lookup"><span data-stu-id="197a9-118">The AS2 Encoder builds the HTTP (and AS2) headers into the `HTTP.UserHttpHeaders` context property.</span></span> <span data-ttu-id="197a9-119">Pour plus d’informations sur ce processus, consultez [de traitement côté envoi d’un Message EDI sortant sur AS2](../core/send-side-processing-of-an-outgoing-edi-message-over-as2.md).</span><span class="sxs-lookup"><span data-stu-id="197a9-119">For more information on this process, see [Send-Side Processing of an Outgoing EDI Message over AS2](../core/send-side-processing-of-an-outgoing-edi-message-over-as2.md).</span></span>  
  
-   <span data-ttu-id="197a9-120">Écrit `HTTP.UserHttpHeaders` dans le contexte.</span><span class="sxs-lookup"><span data-stu-id="197a9-120">Writes `HTTP.UserHttpHeaders` to the context.</span></span>  
  
-   <span data-ttu-id="197a9-121">Compresse le message sortant, si activé.</span><span class="sxs-lookup"><span data-stu-id="197a9-121">Compresses the outgoing message, if enabled.</span></span>  
  
-   <span data-ttu-id="197a9-122">Effectue le traitement MIME, notamment le chiffrement du message (si activé dans le **Message doit être chiffré** propriété d’accord) et d’appliquer une signature numérique (si activé dans le **Message doit être signé**propriétés de l’accord).</span><span class="sxs-lookup"><span data-stu-id="197a9-122">Performs MIME processing, including encrypting the message (if enabled in the **Message should be encrypted** agreement property) and applying a digital signature (if enabled in the **Message should be signed** agreement properties).</span></span> <span data-ttu-id="197a9-123">Le pipeline AS2Send utilise SHA1 ou MD5 pour appliquer la signature, en fonction des paramètres de l'accord.</span><span class="sxs-lookup"><span data-stu-id="197a9-123">The AS2Send pipeline uses either SHA1 or MD5 to apply the signature, based upon agreement settings.</span></span>  
  
-   <span data-ttu-id="197a9-124">Crée un en-tête MIME à disposition de contenu contenant la valeur spécifiée, si la transmission du nom de fichier est active dans les propriétés de l'accord.</span><span class="sxs-lookup"><span data-stu-id="197a9-124">Creates a Content-Disposition MIME header containing the specified value, if transmit file name is enabled in agreement properties.</span></span>  
  
-   <span data-ttu-id="197a9-125">Effectue une copie du message chiffré (au format câble) et la stocke dans la base de données de non-répudiation, si activé dans le **NRR activé pour les messages AS2 encodés sortants** dans les propriétés de l’accord.</span><span class="sxs-lookup"><span data-stu-id="197a9-125">Makes a copy of the encrypted message (in wire format), and stores the copy in the non-repudiation database, if enabled in the **NRR enabled for outbound encoded AS2 messages** in the agreement property.</span></span>  
  
-   <span data-ttu-id="197a9-126">Si un MDN est nécessaire, calcule la valeur MIC et la stocke dans la banque de données.</span><span class="sxs-lookup"><span data-stu-id="197a9-126">If an MDN is required, computes the MIC value and stores it in the data store.</span></span>  
  
-   <span data-ttu-id="197a9-127">Remet le message à l'adaptateur HTTP, lequel écrit les en-têtes à partir de la propriété de contexte UserHTTPHeaders dans le message AS2 sortant.</span><span class="sxs-lookup"><span data-stu-id="197a9-127">Delivers the message to the HTTP adapter, which writes the headers from the UserHTTPHeaders context property into the outgoing AS2 message.</span></span>  
  
-   <span data-ttu-id="197a9-128">Si la fiabilité de la messagerie est nécessaire, renvoie le message jusqu'à réception d'un MDN.</span><span class="sxs-lookup"><span data-stu-id="197a9-128">If reliable messaging is required, resends the message until an MDN is received.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="197a9-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="197a9-129">See Also</span></span>  
 <span data-ttu-id="197a9-130">[Envoi des Messages AS2 par BizTalk Server](../core/how-biztalk-server-sends-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="197a9-130">[How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md) </span></span>  
 [<span data-ttu-id="197a9-131">AS2 Composants d’envoi</span><span class="sxs-lookup"><span data-stu-id="197a9-131">AS2 Send Components</span></span>](../core/as2-send-components.md)