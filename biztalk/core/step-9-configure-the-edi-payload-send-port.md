---
title: "Étape 9 : Configurer le Port d’envoi EDI charge utile | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71a8a4a7-7c3e-4e33-a9c0-a6445a3cc236
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9de1dff24af11cd03cda2550dcab921aec25d585
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-9-configure-the-edi-payload-send-port"></a><span data-ttu-id="0a749-102">Étape 9 : Configurer le Port d’envoi EDI charge utile</span><span class="sxs-lookup"><span data-stu-id="0a749-102">Step 9: Configure the EDI Payload Send Port</span></span>
<span data-ttu-id="0a749-103">![Étape 9 sur 11](../core/media/tut-step9-of-11.gif "Tut_Step9_of_11")</span><span class="sxs-lookup"><span data-stu-id="0a749-103">![Step 9 of 11](../core/media/tut-step9-of-11.gif "Tut_Step9_of_11")</span></span>  
  
 <span data-ttu-id="0a749-104">Dans cette étape, vous configurez un port d’envoi pour envoyer le code XML généré à partir de la charge EDI vers l’application Contoso principale, représentée par le \\_EDIXMLToContoso dossier.</span><span class="sxs-lookup"><span data-stu-id="0a749-104">In this step, you set up a send port to send the XML generated from the EDI payload to the back-end Contoso application, represented by the \\_EDIXMLToContoso folder.</span></span> <span data-ttu-id="0a749-105">Ce port d'envoi utilise un pipeline d'envoi PassThruTransmit.</span><span class="sxs-lookup"><span data-stu-id="0a749-105">This send port uses a PassThruTransmit send pipeline.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0a749-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0a749-106">Prerequisites</span></span>  
 <span data-ttu-id="0a749-107">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0a749-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-create-the-sendpayloadedixml-send-port"></a><span data-ttu-id="0a749-108">Pour créer le port d'envoi Send_Payload_EdiXml</span><span class="sxs-lookup"><span data-stu-id="0a749-108">To create the Send_Payload_EdiXml send port</span></span>  
  
1.  <span data-ttu-id="0a749-109">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="0a749-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-Way Send Port**.</span></span>  
  
2.  <span data-ttu-id="0a749-110">Dans le **propriétés de Port d’envoi** boîte de dialogue Nom de votre port d’envoi **Send_Payload_EdiXml**.</span><span class="sxs-lookup"><span data-stu-id="0a749-110">In the **Send Port Properties** dialog box, name your send port as **Send_Payload_EdiXml**.</span></span> <span data-ttu-id="0a749-111">Sélectionnez **fichier** pour **Type**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="0a749-111">Select **FILE** for **Type**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0a749-112">Le type FILE est spécifié car le pipeline d'envoi n'effectue pas de traitement AS2 sur le fichier de charge.</span><span class="sxs-lookup"><span data-stu-id="0a749-112">The FILE type is specified because the send pipeline is not performing AS2 processing on the payload file.</span></span> <span data-ttu-id="0a749-113">Il s'agit juste d'acheminer le fichier de charge vers un dossier local afin de pouvoir afficher le document informatisé EDI.</span><span class="sxs-lookup"><span data-stu-id="0a749-113">It is just routing the payload file to a local folder so you can see the EDI transaction set.</span></span>  
  
3.  <span data-ttu-id="0a749-114">Dans le **propriétés du Transport FILE** boîte de dialogue, pour **dossier de Destination**, recherchez et sélectionnez [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_EDIXMLToContoso.</span><span class="sxs-lookup"><span data-stu-id="0a749-114">In the **FILE Transport Properties** dialog box, for **Destination folder**, browse to and select [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_EDIXMLToContoso.</span></span> <span data-ttu-id="0a749-115">Laissez **nom de fichier** en tant que **%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="0a749-115">Leave **File name** as **%MessageID%.xml**.</span></span> <span data-ttu-id="0a749-116">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0a749-116">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="0a749-117">Acceptez la valeur par défaut **PassThruTransmit** pour **Pipeline d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="0a749-117">Accept the default of **PassThruTransmit** for **Send Pipeline**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0a749-118">Le pipeline d'envoi PassThruTransmit étant utilisé, le pipeline n'effectue pas de traitement EDI sur le message de charge mais est envoyé au dossier local au format XML produit par le pipeline de réception AS2EdiReceive.</span><span class="sxs-lookup"><span data-stu-id="0a749-118">Because the PassThruTransmit send pipeline is used, the pipeline will not perform any EDI processing on the payload message, but will be sent to the local folder in the XML format produced by the AS2EdiReceive receive pipeline.</span></span>  
  
5.  <span data-ttu-id="0a749-119">Cliquez sur **filtres** dans l’arborescence de la console.</span><span class="sxs-lookup"><span data-stu-id="0a749-119">Click **Filters** in the console tree.</span></span> <span data-ttu-id="0a749-120">Pour **propriété**, entrez **BTS. MessageType**.</span><span class="sxs-lookup"><span data-stu-id="0a749-120">For **Property**, enter **BTS.MessageType**.</span></span> <span data-ttu-id="0a749-121">Pour **opérateur**, entrez  **==** .</span><span class="sxs-lookup"><span data-stu-id="0a749-121">For **Operator**, enter **==**.</span></span> <span data-ttu-id="0a749-122">Pour **valeur**, entrez `http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_864`.</span><span class="sxs-lookup"><span data-stu-id="0a749-122">For **Value**, enter `http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_864`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0a749-123">Ce filtre garantit que ce port d'envoi récupère uniquement les messages de charge 864 X12 dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="0a749-123">This filter ensures that this send port will only pick up X12 864 payload messages from the MessageBox.</span></span>  
  
6.  <span data-ttu-id="0a749-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0a749-124">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="0a749-125">Dans le **Ports d’envoi** volet de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Send_Payload_EdiXml** port d’envoi, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="0a749-125">In the **Send Ports** pane of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send_Payload_EdiXml** send port, and then click **Start**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0a749-126">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0a749-126">Next Steps</span></span>  
 <span data-ttu-id="0a749-127">Vous créez un AS2 et X12 accord entre les deux commerciaux partenaires, comme décrit dans [étape 10 : configurer le X12 et accord de partenariat commercial AS2](../core/step-10-configure-the-x12-and-as2-trading-partner-agreement.md)</span><span class="sxs-lookup"><span data-stu-id="0a749-127">You create an AS2 and X12 agreement between the two trading partners, as described in [Step 10: Configure the X12 and AS2 Trading Partner Agreement](../core/step-10-configure-the-x12-and-as2-trading-partner-agreement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a749-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a749-128">See Also</span></span>  
 [<span data-ttu-id="0a749-129">Didacticiel 3 : Didacticiel AS2</span><span class="sxs-lookup"><span data-stu-id="0a749-129">Tutorial 3: AS2 Tutorial</span></span>](../core/tutorial-3-as2-tutorial.md)