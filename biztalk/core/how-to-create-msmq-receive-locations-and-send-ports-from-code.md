---
title: "Créer MSMQ emplacements de réception et Ports d’envoi à partir de Code | Documents Microsoft"
description: "Créer par programmation MSMQ emplacements de réception et ports d’envoi dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ebb4119-deeb-4287-aa65-7597ff0cc435
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d362ae262c7b054bd86fda72f8aacd3b5ab1455
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-msmq-receive-locations-and-send-ports-programmatically"></a><span data-ttu-id="1cbb8-103">Créer par programme des Ports d’envoi et emplacements de réception MSMQ</span><span class="sxs-lookup"><span data-stu-id="1cbb8-103">Create MSMQ Receive Locations and Send Ports programmatically</span></span>
<span data-ttu-id="1cbb8-104">Cette rubrique décrit l'utilisation de WMI afin de créer un port ou un emplacement pour l'adaptateur MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-104">This topic explains how to use WMI to create a port or location for the MSMQ adapter.</span></span>  
  
 <span data-ttu-id="1cbb8-105">Pour plus d’informations, consultez **création d’un emplacement de réception avec un WMI à l’aide de Configuration de planification Datetime** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="1cbb8-105">For more information, see **Creating a Receive Location with a Datetime Schedule Configuration Using WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="setting-property-values"></a><span data-ttu-id="1cbb8-106">Configuration des valeurs des propriétés</span><span class="sxs-lookup"><span data-stu-id="1cbb8-106">Setting Property Values</span></span>  
 <span data-ttu-id="1cbb8-107">Le processus de création d'un port ou d'un emplacement est toujours le même :</span><span class="sxs-lookup"><span data-stu-id="1cbb8-107">The process of creating a port or location is always the same:</span></span>  
  
1.  <span data-ttu-id="1cbb8-108">Création d'un objet du type approprié.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-108">Create an object of the right type.</span></span>  
  
2.  <span data-ttu-id="1cbb8-109">Définition des valeurs des propriétés sur l'objet.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-109">Set the value of properties on the object.</span></span>  
  
3.  <span data-ttu-id="1cbb8-110">Validation des valeurs de l'objet dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-110">Commit the object values to the database.</span></span>  
  
 <span data-ttu-id="1cbb8-111">Tous les adaptateurs ont certaines propriétés, telles que **nom d’hôte**, en commun.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-111">All adapters have certain properties, such as **HostName**, in common.</span></span> <span data-ttu-id="1cbb8-112">Vous pouvez les définir en les attribuant directement à l'objet.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-112">You set these common properties by directly assigning them to the object.</span></span> <span data-ttu-id="1cbb8-113">Le code C# suivant illustre un cas classique :</span><span class="sxs-lookup"><span data-stu-id="1cbb8-113">The following C# code shows a typical case:</span></span>  
  
```  
objReceiveLocation["HostName"] = "BizTalkServerApplication";  
```  
  
 <span data-ttu-id="1cbb8-114">Vous attribuez des valeurs aux propriétés qui ne sont pas communes à tous les adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-114">You assign values to properties that not all adapters share.</span></span> <span data-ttu-id="1cbb8-115">Pour ce faire, vous devez créer un document XML dans une chaîne, puis attribuer celle-ci à la propriété CustomCfg.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-115">You create an XML document in a string and assign that string to the CustomCfg property.</span></span> <span data-ttu-id="1cbb8-116">Le code C# suivant illustre un cas classique pour un adaptateur FILE :</span><span class="sxs-lookup"><span data-stu-id="1cbb8-116">The following C# code shows a typical case for a FILE adapter:</span></span>  
  
```  
objReceiveLocation["CustomCfg"] =   
        @"<CustomProps>"  
        + @"<BatchSize>20</BatchSize>"  
        + @"<FileMask>*.xml</FileMask>"  
        + @"<FileNetFailRetryCount>5</FileNetFailRetryCount>"  
        + @"<FileNetFailRetryInt>5</FileNetFailRetryInt>"  
        + @"</CustomProps>";  
```  
  
 <span data-ttu-id="1cbb8-117">Les noms des balises présentes dans l'élément CustomProps représentent les noms internes que l'adaptateur utilise pour les propriétés.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-117">The names of the tags in the CustomProps element are the internal names that the adapter uses for the properties.</span></span>  
  
 <span data-ttu-id="1cbb8-118">L'adaptateur MSMQ possède une balise unique, AdapterConfig, qui se trouve à l'intérieur de la balise CustomProps.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-118">The MSMQ adapter has a single tag, AdapterConfig, inside the CustomProps tag.</span></span> <span data-ttu-id="1cbb8-119">La balise AdapterConfig contient une chaîne de balises XML pour les valeurs des propriétés personnalisées incluses dans une balise Config.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-119">The AdapterConfig tag contains a string of XML tags for the custom property values enclosed in a Config tag.</span></span> <span data-ttu-id="1cbb8-120">Toutefois, les balises sont codées : «&lt;« remplace »\<« et »&gt;» remplace « > ».</span><span class="sxs-lookup"><span data-stu-id="1cbb8-120">However, the tags are encoded: "&lt;" replaces "\<" and "&gt;" replaces ">".</span></span> <span data-ttu-id="1cbb8-121">Par exemple, le XML d'un sous-ensemble de l'adaptateur associé à des propriétés MSMQ peut s'afficher comme suit :</span><span class="sxs-lookup"><span data-stu-id="1cbb8-121">For example, the XML for a subset of the adapter for MSMQ properties might appear as follows:</span></span>  
  
```  
<Config>  
    <batchSize>40</batchSize>  
</Config>  
```  
  
 <span data-ttu-id="1cbb8-122">Notez que la **vt** attribut n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-122">Notice that the **vt** attribute is not used.</span></span> <span data-ttu-id="1cbb8-123">La chaîne assignée à la **CustomCfg** propriété s’affiche comme suit après avoir :</span><span class="sxs-lookup"><span data-stu-id="1cbb8-123">The string assigned to the **CustomCfg** property appears as follows after encoding:</span></span>  
  
```  
<CustomProps><AdapterConfig vt="8"><Config><batchSize>40</batchSize></Config></AdapterConfig></CustomProps>  
```  
  
## <a name="custom-property-names"></a><span data-ttu-id="1cbb8-124">Noms des propriétés personnalisées</span><span class="sxs-lookup"><span data-stu-id="1cbb8-124">Custom Property Names</span></span>  
 <span data-ttu-id="1cbb8-125">Le tableau suivant répertorie les noms internes de l’adaptateur MSMQ **envoyer** propriétés personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-125">The following table describes the internal names of the MSMQ adapter **Send** custom properties.</span></span>  
  
|<span data-ttu-id="1cbb8-126">**Envoyer le nom de propriété personnalisée**</span><span class="sxs-lookup"><span data-stu-id="1cbb8-126">**Send custom property name**</span></span>|<span data-ttu-id="1cbb8-127">**Nom complet**</span><span class="sxs-lookup"><span data-stu-id="1cbb8-127">**Display name**</span></span>|  
|-----------------------------------|----------------------|  
|<span data-ttu-id="1cbb8-128">acknowledgeType</span><span class="sxs-lookup"><span data-stu-id="1cbb8-128">acknowledgeType</span></span>|<span data-ttu-id="1cbb8-129">Type d'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="1cbb8-129">Acknowledgement Type</span></span>|  
|<span data-ttu-id="1cbb8-130">administrationQueue</span><span class="sxs-lookup"><span data-stu-id="1cbb8-130">administrationQueue</span></span>|<span data-ttu-id="1cbb8-131">File d'attente d'administration</span><span class="sxs-lookup"><span data-stu-id="1cbb8-131">Administration Queue</span></span>|  
|<span data-ttu-id="1cbb8-132">certificate</span><span class="sxs-lookup"><span data-stu-id="1cbb8-132">certificate</span></span>|<span data-ttu-id="1cbb8-133">Empreinte de certificat</span><span class="sxs-lookup"><span data-stu-id="1cbb8-133">Certificate Thumbprint</span></span>|  
|<span data-ttu-id="1cbb8-134">encryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="1cbb8-134">encryptionAlgorithm</span></span>|<span data-ttu-id="1cbb8-135">Algorithme de chiffrement</span><span class="sxs-lookup"><span data-stu-id="1cbb8-135">Encryption Algorithm</span></span>|  
|<span data-ttu-id="1cbb8-136">maximumMessageSize</span><span class="sxs-lookup"><span data-stu-id="1cbb8-136">maximumMessageSize</span></span>|<span data-ttu-id="1cbb8-137">Taille maximale message (en Ko)</span><span class="sxs-lookup"><span data-stu-id="1cbb8-137">Maximum Message Size (in KB)</span></span>|  
|<span data-ttu-id="1cbb8-138">password</span><span class="sxs-lookup"><span data-stu-id="1cbb8-138">password</span></span>|<span data-ttu-id="1cbb8-139">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="1cbb8-139">Password</span></span>|  
|<span data-ttu-id="1cbb8-140">priority</span><span class="sxs-lookup"><span data-stu-id="1cbb8-140">priority</span></span>|<span data-ttu-id="1cbb8-141">Priorité du message</span><span class="sxs-lookup"><span data-stu-id="1cbb8-141">Message Priority</span></span>|  
|<span data-ttu-id="1cbb8-142">queue</span><span class="sxs-lookup"><span data-stu-id="1cbb8-142">queue</span></span>|<span data-ttu-id="1cbb8-143">File d’attente de destination</span><span class="sxs-lookup"><span data-stu-id="1cbb8-143">Destination Queue</span></span>|  
|<span data-ttu-id="1cbb8-144">recoverable</span><span class="sxs-lookup"><span data-stu-id="1cbb8-144">recoverable</span></span>|<span data-ttu-id="1cbb8-145">Récupérable</span><span class="sxs-lookup"><span data-stu-id="1cbb8-145">Recoverable</span></span>|  
|<span data-ttu-id="1cbb8-146">segmentationSupport</span><span class="sxs-lookup"><span data-stu-id="1cbb8-146">segmentationSupport</span></span>|<span data-ttu-id="1cbb8-147">Prise en charge de la segmentation</span><span class="sxs-lookup"><span data-stu-id="1cbb8-147">Support Segmentation</span></span>|  
|<span data-ttu-id="1cbb8-148">sendBatchSize</span><span class="sxs-lookup"><span data-stu-id="1cbb8-148">sendBatchSize</span></span>|<span data-ttu-id="1cbb8-149">Taille de lot</span><span class="sxs-lookup"><span data-stu-id="1cbb8-149">Batch Size</span></span>|  
|<span data-ttu-id="1cbb8-150">sendQueueName</span><span class="sxs-lookup"><span data-stu-id="1cbb8-150">sendQueueName</span></span>|<span data-ttu-id="1cbb8-151">File d’attente de destination</span><span class="sxs-lookup"><span data-stu-id="1cbb8-151">Destination Queue</span></span>|  
|<span data-ttu-id="1cbb8-152">timeOut</span><span class="sxs-lookup"><span data-stu-id="1cbb8-152">timeOut</span></span>|<span data-ttu-id="1cbb8-153">Délai d'expiration</span><span class="sxs-lookup"><span data-stu-id="1cbb8-153">Timeout</span></span>|  
|<span data-ttu-id="1cbb8-154">timeOutUnits</span><span class="sxs-lookup"><span data-stu-id="1cbb8-154">timeOutUnits</span></span>|<span data-ttu-id="1cbb8-155">Unité délai d'expiration</span><span class="sxs-lookup"><span data-stu-id="1cbb8-155">Timeout Unit</span></span>|  
|<span data-ttu-id="1cbb8-156">transactionnels</span><span class="sxs-lookup"><span data-stu-id="1cbb8-156">transactional</span></span>|<span data-ttu-id="1cbb8-157">Transactionnelle</span><span class="sxs-lookup"><span data-stu-id="1cbb8-157">Transactional</span></span>|  
|<span data-ttu-id="1cbb8-158">useAuthentication</span><span class="sxs-lookup"><span data-stu-id="1cbb8-158">useAuthentication</span></span>|<span data-ttu-id="1cbb8-159">Utiliser l'authentification</span><span class="sxs-lookup"><span data-stu-id="1cbb8-159">Use Authentication</span></span>|  
|<span data-ttu-id="1cbb8-160">useDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="1cbb8-160">useDeadLetterQueue</span></span>|<span data-ttu-id="1cbb8-161">Utiliser file d'attente messages non distribués</span><span class="sxs-lookup"><span data-stu-id="1cbb8-161">Use Dead Letter Queue</span></span>|  
|<span data-ttu-id="1cbb8-162">useJournalQueue</span><span class="sxs-lookup"><span data-stu-id="1cbb8-162">useJournalQueue</span></span>|<span data-ttu-id="1cbb8-163">Utiliser file d'attente journal</span><span class="sxs-lookup"><span data-stu-id="1cbb8-163">Use Journal Queue</span></span>|  
|<span data-ttu-id="1cbb8-164">userName</span><span class="sxs-lookup"><span data-stu-id="1cbb8-164">userName</span></span>|<span data-ttu-id="1cbb8-165">Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1cbb8-165">User Name</span></span>|  
  
 <span data-ttu-id="1cbb8-166">Le tableau suivant répertorie les noms internes de l’adaptateur MSMQ **réception** propriétés personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-166">The following table describes the internal names of the MSMQ adapter **Receive** custom properties.</span></span>  
  
|<span data-ttu-id="1cbb8-167">**Nom de la propriété personnalisée de réception**</span><span class="sxs-lookup"><span data-stu-id="1cbb8-167">**Receive custom property name**</span></span>|<span data-ttu-id="1cbb8-168">**Nom complet**</span><span class="sxs-lookup"><span data-stu-id="1cbb8-168">**Display name**</span></span>|  
|--------------------------------------|----------------------|  
|<span data-ttu-id="1cbb8-169">batchSize</span><span class="sxs-lookup"><span data-stu-id="1cbb8-169">batchSize</span></span>|<span data-ttu-id="1cbb8-170">Taille de lot</span><span class="sxs-lookup"><span data-stu-id="1cbb8-170">Batch Size</span></span>|  
|<span data-ttu-id="1cbb8-171">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="1cbb8-171">Password</span></span>|<span data-ttu-id="1cbb8-172">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="1cbb8-172">Password</span></span>|  
|<span data-ttu-id="1cbb8-173">File d'attente</span><span class="sxs-lookup"><span data-stu-id="1cbb8-173">Queue</span></span>|<span data-ttu-id="1cbb8-174">File d'attente</span><span class="sxs-lookup"><span data-stu-id="1cbb8-174">Queue</span></span>|  
|<span data-ttu-id="1cbb8-175">serialProcessing</span><span class="sxs-lookup"><span data-stu-id="1cbb8-175">serialProcessing</span></span>|<span data-ttu-id="1cbb8-176">Traitement en série</span><span class="sxs-lookup"><span data-stu-id="1cbb8-176">Serial Processing</span></span>|  
|<span data-ttu-id="1cbb8-177">Transactionnelle</span><span class="sxs-lookup"><span data-stu-id="1cbb8-177">Transactional</span></span>|<span data-ttu-id="1cbb8-178">Transactionnelle</span><span class="sxs-lookup"><span data-stu-id="1cbb8-178">Transactional</span></span>|  
|<span data-ttu-id="1cbb8-179">userName</span><span class="sxs-lookup"><span data-stu-id="1cbb8-179">userName</span></span>|<span data-ttu-id="1cbb8-180">Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1cbb8-180">User Name</span></span>|  
  
## <a name="sample-code"></a><span data-ttu-id="1cbb8-181">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="1cbb8-181">Sample Code</span></span>  
 <span data-ttu-id="1cbb8-182">Le programme C# suivant permet de créer un emplacement de réception unique pour l'adaptateur MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-182">The following C# program creates a single receive location for the MSMQ adapter.</span></span> <span data-ttu-id="1cbb8-183">Il considère que le port de réception, à savoir ReceivePort1, existe et utilise une fonction d'assistance pour coder et mettre en forme les propriétés personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1cbb8-183">It assumes that the receive port, ReceivePort1, exists and uses a helper function to encode and format the custom properties.</span></span>  
  
```  
using System;  
using System.Management;  
using System.Text;  
  
namespace CreateReceive  
{  
    ///   
    /// Program to create a receive location.  
    ///   
    class CreateReceive  
    {  
        /// The main entry point for the application.  
  
        [STAThread]  
        static void Main()  
        {  
            // Custom properties & values  
            string cfg =   
                    @"<queue>FORMATNAME:DIRECT=OS:MYMACHINE02\PRIVATE$\QUEUE2</queue>"  
                    + @"<batchSize>40</batchSize>"  
                    + @"<transactional>true</transactional>"  
                    + @"<serialProcessing>false</serialProcessing>";  
  
            CreateReceiveLocation (  
                    "Code Created Location",  
                    "ReceivePort1",  
                    "MSMQ",  
                    "BizTalkServerApplication",  
                    EncodeCustomProps(cfg),  // Encode the custom props  
                    "Microsoft.BizTalk.DefaultPipelines.PassThruReceive,"   
                            + " Microsoft.BizTalk.DefaultPipelines,"   
                            + " Version=3.0.1.0, Culture=neutral,"   
                            + " PublicKeyToken=31bf3856ad364e35",  
                    @"FORMATNAME:DIRECT=OS:MYMACHINE\PRIVATE$\QUEUE2"  
                );  
  
        }  
  
        static string EncodeCustomProps (string cp) {  
  
            // Enclose the properties and values in a Config> tag.  
            StringBuilder tmp = new StringBuilder( @"<Config>" + cp + @"</Config>");  
  
            // Encode the string  
            tmp = tmp.Replace("<","<");  
            tmp = tmp.Replace(">",">");  
  
            return (  
                // Enclose the encoded string with necessary tags  
                "<CustomProps><AdapterConfig vt=\"8\">"  
                + tmp.ToString()   
                + "</AdapterConfig></CustomProps>");  
  
        }  
  
        static void CreateReceiveLocation (  
            string name,            // Location name  
            string port,            // Receive port, already exists  
            string adapterName,     // The transport type  
            string hostName,        // BTS host  
            string customCfg,       // Encoded custom properties  
            string pipeline,        // Full specification of pipeline  
            string inboundTransport)// Inbound transport url  
        {  
            try   
            {  
                // Create options to store options in management object  
                PutOptions options = new PutOptions();  
                options.Type = PutType.CreateOnly;  
  
                // Create a management object  
                // Get the class  
                ManagementClass objReceiveLocationClass =   
                           new ManagementClass(  
                               "root\\MicrosoftBizTalkServer",   
                               "MSBTS_ReceiveLocation",   
                               null);  
                // Create an instance of the member of the class  
                ManagementObject objReceiveLocation =  
                          objReceiveLocationClass.CreateInstance();  
  
                // Fill in the properties  
                objReceiveLocation["Name"] = name;  
                objReceiveLocation["ReceivePortName"] = port;  
                objReceiveLocation["AdapterName"] = adapterName;  
                objReceiveLocation["HostName"] = hostName;  
                objReceiveLocation["PipelineName"] = pipeline;  
                objReceiveLocation["CustomCfg"] = customCfg;  
                objReceiveLocation["IsDisabled"] = true;  
                objReceiveLocation["InBoundTransportURL"] = inboundTransport;  
  
                // Put the options -- creates the receive location  
                objReceiveLocation.Put(options);  
            }  
            catch (Exception excep)  
            {  
                System.Console.WriteLine("Create Receive Location ({0}) failed - {1}",  
                                                name, excep.Message);  
            }  
        }  
    }  
}  
```