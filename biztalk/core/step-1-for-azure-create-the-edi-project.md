---
title: "Étape 1 (pour Azure) : Créer le projet EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d353129-04f0-456b-b371-b346959f5155
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb5f2e7af54ef99acff37a350c5fa7d9ba65af5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-for-azure-create-the-edi-project"></a><span data-ttu-id="0ece2-102">Étape 1 (pour Azure) : Créer le projet EDI</span><span class="sxs-lookup"><span data-stu-id="0ece2-102">Step 1 (For Azure): Create the EDI Project</span></span>
<span data-ttu-id="0ece2-103">Dans cette section, Contoso utilise la version de l’[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] d’avril 2012 pour créer un projet EDI.</span><span class="sxs-lookup"><span data-stu-id="0ece2-103">In this section, Contoso creates an EDI project using the [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] April 2012 release.</span></span> <span data-ttu-id="0ece2-104">Dans le cadre du projet, Contoso ajoute les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0ece2-104">As part of the project, Contoso adds the following:</span></span>  
  
-   <span data-ttu-id="0ece2-105">Un schéma de commande client interne (**ECommerceSalesOrder.xsd**) à laquelle le X12 sera transformé le schéma de commande client EDI 840.</span><span class="sxs-lookup"><span data-stu-id="0ece2-105">An internal sales order schema (**ECommerceSalesOrder.xsd**) to which the X12 840 EDI sales order schema will be transformed.</span></span> <span data-ttu-id="0ece2-106">Contoso utilise le schéma interne pour traiter le message après sa réception dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;</span><span class="sxs-lookup"><span data-stu-id="0ece2-106">Contoso uses the internal schema to process the message after it is received into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="0ece2-107">Une transformation (**EDI840TOSALESORDER. TRFM**) pour convertir le X12 840 ventes schéma à la **ECommerceSalesOrder** schéma.</span><span class="sxs-lookup"><span data-stu-id="0ece2-107">A transform (**EDI840TOSALESORDER.TRFM**) to convert the X12 840 sales order schema to the **ECommerceSalesOrder** schema.</span></span>  
  
 <span data-ttu-id="0ece2-108">Contoso utilise ces artefacts lors de la création d’un accord dans le portail Azure BizTalk dans l’[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0ece2-108">Contoso uses these artifacts while creating an agreement in the Azure BizTalk portal in [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)].</span></span>  
  
### <a name="to-create-edi-project"></a><span data-ttu-id="0ece2-109">Pour créer un projet EDI</span><span class="sxs-lookup"><span data-stu-id="0ece2-109">To create EDI project</span></span>  
  
1.  <span data-ttu-id="0ece2-110">Ouvrez [!INCLUDE[vs2010](../includes/vs2010-md.md)], à partir de la **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="0ece2-110">Open [!INCLUDE[vs2010](../includes/vs2010-md.md)], from the **File** menu point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="0ece2-111">Dans le **nouveau projet** boîte de dialogue, à partir de la **modèles installés**, sélectionnez **Service Bus**.</span><span class="sxs-lookup"><span data-stu-id="0ece2-111">In the **New Project** dialog box, from the **Installed Templates**, select **Service Bus**.</span></span> <span data-ttu-id="0ece2-112">Spécifiez un nom de projet et un emplacement pour le projet, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0ece2-112">Specify a project name and a location for the project, and then click **OK**.</span></span>  
  
##  <span data-ttu-id="0ece2-113"><a name="BKMK_CreateSchema"></a>Pour créer un schéma dans le projet EDI</span><span class="sxs-lookup"><span data-stu-id="0ece2-113"><a name="BKMK_CreateSchema"></a> To create a schema within the EDI project</span></span>  
  
1.  <span data-ttu-id="0ece2-114">À partir de l’Explorateur de solutions, cliquez sur le nom de projet que vous venez de créer, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="0ece2-114">From the Solution Explorer, right-click the project name you just created, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="0ece2-115">Dans le **ajouter un nouvel élément** boîte de dialogue, à partir de la **modèles installés**, sélectionnez **schéma**, spécifiez le nom du schéma en tant que **ECommerceSalesOrder.xsd**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0ece2-115">In the **Add New Item** dialog box, from the **Installed Templates**, select **Schema**, specify the name of the schema as **ECommerceSalesOrder.xsd**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="0ece2-116">Modifiez et construisez le schéma pour qu’il ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="0ece2-116">Edit and build the schema to resemble the following:</span></span>  
  
    ```  
    \<?xml version="1.0" encoding="utf-16"?>  
    \<xs:schema xmlns="http://ECommerceSalesOrder.Inbound" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://ECommerceSalesOrder.Inbound" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      \<xs:element name="SalesOrder">  
        \<xs:complexType>  
          \<xs:sequence>  
            \<xs:element name="CompanyCode" type="xs:string" />  
            \<xs:element name="PartID" type="xs:int" />  
            \<xs:element name="Quantity" type="xs:int" />  
            \<xs:element name="AskPrice" type="xs:decimal" />  
            \<xs:element name="RequestShipmentDate" type="xs:date" />  
            \<xs:element name="Address">  
              \<xs:complexType>  
                \<xs:sequence>  
                  \<xs:element name="Line1" type="xs:string" />  
                  \<xs:element name="Line2" type="xs:string" />  
                  \<xs:element name="City" type="xs:string" />  
                  \<xs:element name="State" type="xs:string" />  
                  \<xs:element name="Country" type="xs:string" />  
                  \<xs:element name="Zipcode" type="xs:int" />  
                \</xs:sequence>  
              \</xs:complexType>  
            \</xs:element>  
            \<xs:element name="Contact">  
              \<xs:complexType>  
                \<xs:sequence>  
                  \<xs:element name="Firstname" type="xs:string" />  
                  \<xs:element name="Lastname" type="xs:string" />  
                \</xs:sequence>  
              \</xs:complexType>  
            \</xs:element>  
            \<xs:element name="Comments" type="xs:string" />  
            \<xs:element name="DateNow" type="xs:date" />  
          \</xs:sequence>  
        \</xs:complexType>  
      \</xs:element>  
    \</xs:schema>  
    ```  
  
     <span data-ttu-id="0ece2-117">Vous pouvez utiliser l’Éditeur de schéma pour construire ce schéma.</span><span class="sxs-lookup"><span data-stu-id="0ece2-117">You can use the Schema Editor to build this schema.</span></span> <span data-ttu-id="0ece2-118">Pour plus d’informations, consultez [à l’aide de l’Éditeur BizTalk](../core/using-biztalk-editor.md).</span><span class="sxs-lookup"><span data-stu-id="0ece2-118">For more information, see [Using BizTalk Editor](../core/using-biztalk-editor.md).</span></span>  
  
4.  <span data-ttu-id="0ece2-119">Enregistrez le schéma.</span><span class="sxs-lookup"><span data-stu-id="0ece2-119">Save the schema.</span></span>  
  
##  <span data-ttu-id="0ece2-120"><a name="BKMK_CreateTrfm"></a>Pour créer une transformation dans le projet EDI</span><span class="sxs-lookup"><span data-stu-id="0ece2-120"><a name="BKMK_CreateTrfm"></a> To create a transform within the EDI project</span></span>  
  
1.  <span data-ttu-id="0ece2-121">À partir de l’Explorateur de solutions, cliquez sur le nom de projet que vous venez de créer, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="0ece2-121">From the Solution Explorer, right-click the project name you just created, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="0ece2-122">Dans le **ajouter un nouvel élément** boîte de dialogue, à partir de la **modèles installés**, sélectionnez **carte**, spécifiez le nom du schéma en tant que **Edi840ToSalesOrder.trfm**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0ece2-122">In the **Add New Item** dialog box, from the **Installed Templates**, select **Map**, specify the name of the schema as **Edi840ToSalesOrder.trfm**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="0ece2-123">Dans le mappage, pour le schéma source, sélectionnez **X12_00401_840.xsd**.</span><span class="sxs-lookup"><span data-stu-id="0ece2-123">In the map, for the source schema select **X12_00401_840.xsd**.</span></span> <span data-ttu-id="0ece2-124">Il s’agit du schéma X12 standard pour une commande client EDI.</span><span class="sxs-lookup"><span data-stu-id="0ece2-124">This is the standard X12 schema for an EDI sales order.</span></span> <span data-ttu-id="0ece2-125">Ce schéma doit être déjà ajouté au projet EDI que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="0ece2-125">You must have already added this schema to the EDI project you created.</span></span> <span data-ttu-id="0ece2-126">Vous pouvez télécharger cette et autres X12 schémas à partir de [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057).</span><span class="sxs-lookup"><span data-stu-id="0ece2-126">You can download this, and other X12 schemas from [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057).</span></span> <span data-ttu-id="0ece2-127">Le X12 schémas font partie de la **MicrosoftEdiXSDTemplates.zip** package disponible à partir de l’emplacement de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="0ece2-127">The X12 schemas are part of the **MicrosoftEdiXSDTemplates.zip** package available from the download location.</span></span>  
  
4.  <span data-ttu-id="0ece2-128">Pour le schéma de destination, sélectionnez **ECommerceSalesOrder.xsd**.</span><span class="sxs-lookup"><span data-stu-id="0ece2-128">For the destination schema, select **ECommerceSalesOrder.xsd**.</span></span> <span data-ttu-id="0ece2-129">Vous avez créé ce schéma auparavant dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0ece2-129">You created this schema earlier in this topic.</span></span>  
  
5.  <span data-ttu-id="0ece2-130">Créez le mappage en connectant les nœuds pertinents dans les schémas source et cible.</span><span class="sxs-lookup"><span data-stu-id="0ece2-130">Create the map by connecting the relevant nodes in the source and target schemas.</span></span>  
  
6.  <span data-ttu-id="0ece2-131">Enregistrez le mappage.</span><span class="sxs-lookup"><span data-stu-id="0ece2-131">Save the map.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ece2-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ece2-132">See Also</span></span>  
 [<span data-ttu-id="0ece2-133">Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="0ece2-133">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)