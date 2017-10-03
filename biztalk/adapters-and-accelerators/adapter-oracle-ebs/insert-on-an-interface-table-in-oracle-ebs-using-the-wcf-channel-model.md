---
title: "Exécuter une opération d’insertion sur une table d’interface dans Oracle E-Business Suite à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a2e5ee3-552b-40a2-aaa6-5391347f1146
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 703b00adeb373fe66c4a96c324f13f9c3c5ec655
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-an-insert-operation-on-an-interface-table-in-oracle-e-business-suite-using-the-wcf-channel-model"></a><span data-ttu-id="3f053-102">Exécuter une opération d’insertion sur une table d’interface dans Oracle E-Business Suite à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="3f053-102">Run an insert operation on an interface table in Oracle E-Business Suite using the WCF channel model</span></span>
<span data-ttu-id="3f053-103">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] détecte un ensemble d’opérations Insert, Select, Update et Delete sur les tables d’interface Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="3f053-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] discovers a set of Insert, Select, Update, and Delete operations on Oracle E-Business Suite interface tables.</span></span> <span data-ttu-id="3f053-104">À l’aide de ces opérations, vous pouvez effectuer simple Insert, Select, Update et supprimer les instructions qualifiées par Where clause sur une table d’interface cible.</span><span class="sxs-lookup"><span data-stu-id="3f053-104">By using these operations, you can perform simple Insert, Select, Update, and Delete statements qualified by a Where clause on a target interface table.</span></span> <span data-ttu-id="3f053-105">Cette rubrique fournit des instructions sur la façon d’effectuer une opération d’insertion sur une table d’interface à l’aide du modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="3f053-105">This topic provides instructions on how to perform an Insert operation on an interface table using the WCF channel model.</span></span>  
  
 <span data-ttu-id="3f053-106">Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [opérations sur les Tables d’Interface et les vues de l’Interface](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md).</span><span class="sxs-lookup"><span data-stu-id="3f053-106">For more information on how the adapter supports these operations, see [Operations on Interface Tables and Interface Views](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md).</span></span> <span data-ttu-id="3f053-107">Pour plus d’informations sur la façon d’effectuer des opérations sur Oracle E-Business Suite à l’aide du modèle de canal WCF, consultez [vue d’ensemble du modèle de canal WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="3f053-107">For more information about how to perform operations on Oracle E-Business Suite using the WCF Channel model, see [Overview of the WCF channel model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="3f053-108">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="3f053-108">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="3f053-109">L’exemple de cette rubrique effectue des opérations sur la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="3f053-109">The example in this topic performs operations on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="3f053-110">La table est créée en exécutant le script fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="3f053-110">The table is created by running the script provided with the samples.</span></span> <span data-ttu-id="3f053-111">Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="3f053-111">For more information about samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="3f053-112">Un exemple, **InsertOperation**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="3f053-112">A sample, **InsertOperation**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-insert-message"></a><span data-ttu-id="3f053-113">Le Message d’insertion</span><span class="sxs-lookup"><span data-stu-id="3f053-113">The Insert Message</span></span>  
 <span data-ttu-id="3f053-114">Pour effectuer des opérations sur Oracle E-Business Suite à l’aide du modèle de canal WCF, vous devez disposer du message de demande spécifique à l’opération.</span><span class="sxs-lookup"><span data-stu-id="3f053-114">To perform operations on the Oracle E-Business Suite using the WCF channel model, you must have the request message specific to the operation.</span></span> <span data-ttu-id="3f053-115">Le message de demande pour effectuer une opération d’insertion sur la table d’interface MS_SAMPLE_EMPLOYEE ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="3f053-115">The request message to perform an Insert operation on the MS_SAMPLE_EMPLOYEE interface table resembles the following:</span></span>  
  
```  
<Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE">  
  <RECORDSET>  
    <InsertRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/APPS/MS_SAMPLE_EMPLOYEE">  
      <EMP_NO>10050</EMP_NO>  
      <NAME>John Smith</NAME>  
      <DESIGNATION>Manager</DESIGNATION>  
      <SALARY>500000</SALARY>  
      <JOIN_DATE>1999-05-31</JOIN_DATE>  
    </InsertRecord>  
  </RECORDSET>  
</Insert>  
```  
  
 <span data-ttu-id="3f053-116">Ce message de demande insère un enregistrement avec les détails suivants :</span><span class="sxs-lookup"><span data-stu-id="3f053-116">This request message inserts a record with following details:</span></span>  
  
```  
Employee Number = 10050  
Name = Tom Smith  
Designation = Manager  
Salary = 500000  
```  
  
 <span data-ttu-id="3f053-117">Vous devez copier le message vers un fichier, par exemple, InsertRequest.xml.</span><span class="sxs-lookup"><span data-stu-id="3f053-117">You must copy the message to a file, e.g. InsertRequest.xml.</span></span> <span data-ttu-id="3f053-118">Ce fichier est utilisé dans cet exemple pour envoyer le message de demande pour Oracle E-Business Suite à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f053-118">This file is used in this example to send the request message to Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="3f053-119">Pour plus d’informations sur le schéma de message pour les opérations sur la table, consultez [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md).</span><span class="sxs-lookup"><span data-stu-id="3f053-119">For more information about the message schema for operations on table, see [Message Schemas for Insert, Update, Delete, and Select Operations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md).</span></span>  
  
## <a name="creating-a-wcf-channel-application"></a><span data-ttu-id="3f053-120">Création d’une Application de canal WCF</span><span class="sxs-lookup"><span data-stu-id="3f053-120">Creating a WCF Channel Application</span></span>  
 <span data-ttu-id="3f053-121">Cette section fournit des instructions sur la création d’une application de canal WCF pour effectuer une opération d’insertion sur la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="3f053-121">This section provides instructions on how to create a WCF channel application to perform an Insert operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
#### <a name="to-create-a-wcf-channel-application-for-inserting-records-into-the-table"></a><span data-ttu-id="3f053-122">Pour créer une application de canal WCF pour insérer des enregistrements dans la table</span><span class="sxs-lookup"><span data-stu-id="3f053-122">To create a WCF channel application for inserting records into the table</span></span>  
  
1.  <span data-ttu-id="3f053-123">Créez un projet Visual c# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3f053-123">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="3f053-124">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="3f053-124">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="3f053-125">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, et `System.Runtime.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="3f053-125">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.</span></span>  
  
3.  <span data-ttu-id="3f053-126">Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="3f053-126">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `Microsoft.ServiceModel.Channels`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  <span data-ttu-id="3f053-127">Créer la liaison et le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="3f053-127">Create the binding and endpoint.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
  
    ```  
  
5.  <span data-ttu-id="3f053-128">Étant donné que vous effectuez une opération sur une table d’interface, vous devez définir le contexte d’application.</span><span class="sxs-lookup"><span data-stu-id="3f053-128">Because you are performing an operation on an interface table, you must set the application context.</span></span> <span data-ttu-id="3f053-129">Dans cet exemple, pour définir le contexte d’application, que vous spécifiez la **OracleUserName**, **OraclePassword**, et **OracleEBSResponsibilityName** propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="3f053-129">In this example, to set the application context, you specify the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="3f053-130">Pour plus d’informations sur le contexte de l’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span><span class="sxs-lookup"><span data-stu-id="3f053-130">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
6.  <span data-ttu-id="3f053-131">Créez et ouvrez la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="3f053-131">Create and open the channel factory.</span></span> <span data-ttu-id="3f053-132">Cette application envoie un message de demande pour Oracle E-Business Suite et reçoit une réponse, donc vous devez implémenter l’interface IRequestChannel.</span><span class="sxs-lookup"><span data-stu-id="3f053-132">This application sends request message to Oracle E-Business Suite and receives a response, hence you must implement the IRequestChannel interface.</span></span>  
  
    ```  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    factory.Credentials.UserName.UserName = "<Enter user name here>";  
    factory.Credentials.UserName.Password = "<Enter password here>";  
    factory.Open();  
    ```  
  
7.  <span data-ttu-id="3f053-133">Créer et ouvrir le canal.</span><span class="sxs-lookup"><span data-stu-id="3f053-133">Create and open the channel.</span></span>  
  
    ```  
    IRequestChannel channel;  
    try  
    {  
       channel = factory.CreateChannel();  
       channel.Open();  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception :" + ex.Message);  
       throw;  
    }  
    ```  
  
8.  <span data-ttu-id="3f053-134">Créer et envoyer le message de demande.</span><span class="sxs-lookup"><span data-stu-id="3f053-134">Create and send the request message.</span></span>  
  
    ```  
    XmlReader readerIn;  
    try  
    {  
       readerIn = XmlReader.Create("InsertRequest.xml");  
       Console.WriteLine("Reader created");  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    Message messageIn;  
    Message messageOut;  
    try  
    {  
       messageIn = Message.CreateMessage(MessageVersion.Default, "InterfaceTables/Insert/FND/APPS/MS_SAMPLE_EMPLOYEE", readerIn);  
       messageOut = channel.Request(messageIn);  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
  
    ```  
  
     <span data-ttu-id="3f053-135">Lors de la création du message de demande, vous devez spécifier l’action du message qui indique l’action que l’adaptateur effectue sur la table d’interface.</span><span class="sxs-lookup"><span data-stu-id="3f053-135">While creating the request message, you must specify the message action that indicates the action that the adapter performs on the interface table.</span></span> <span data-ttu-id="3f053-136">Pour effectuer une opération d’insertion sur la table MS_SAMPLE_EMPLOYEE, l’action du message est `InterfaceTables/Insert/FND/APPS/MS_SAMPLE_EMPLOYEE`.</span><span class="sxs-lookup"><span data-stu-id="3f053-136">To perform an Insert operation on the MS_SAMPLE_EMPLOYEE table, the message action is `InterfaceTables/Insert/FND/APPS/MS_SAMPLE_EMPLOYEE`.</span></span> <span data-ttu-id="3f053-137">Pour plus d’informations sur la façon dont vous pouvez déterminer l’action du message pour différentes opérations sur les tables, consultez [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md).</span><span class="sxs-lookup"><span data-stu-id="3f053-137">For information about how you can determine the message action for various operations on tables, see [Message Schemas for Insert, Update, Delete, and Select Operations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md).</span></span>  
  
9. <span data-ttu-id="3f053-138">Obtenir le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="3f053-138">Get the response message.</span></span>  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    XmlDocument doc = new XmlDocument();  
    doc.Load(readerOut);  
    doc.Save("C:\\Response.xml");  
    ```  
  
10. <span data-ttu-id="3f053-139">Fermez le message, le canal et la fabrique de canaux.</span><span class="sxs-lookup"><span data-stu-id="3f053-139">Close the message, channel, and channel factory.</span></span>  
  
    ```  
    messageOut.Close();  
    channel.Close();  
    factory.Close();  
    ```  
  
11. <span data-ttu-id="3f053-140">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="3f053-140">Build the project.</span></span> <span data-ttu-id="3f053-141">Après avoir généré le projet, vous devez copier le message de demande, InsertRequest.xml, au même emplacement que votre projet exécutable.</span><span class="sxs-lookup"><span data-stu-id="3f053-141">After building the project, you must copy the request message, InsertRequest.xml, at the same location as your project executable.</span></span> <span data-ttu-id="3f053-142">En règle générale, cet emplacement est \bin\Debug\ sous le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="3f053-142">Typically, this location is \bin\Debug\ under your project directory.</span></span>  
  
12. <span data-ttu-id="3f053-143">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="3f053-143">Run the application.</span></span> <span data-ttu-id="3f053-144">Le message de réponse, Response.xml, est enregistré dans l’emplacement spécifié dans l’application.</span><span class="sxs-lookup"><span data-stu-id="3f053-144">The response message, Response.xml, is saved at the location you specified in the application.</span></span> <span data-ttu-id="3f053-145">Le message de réponse contient le numéro ou les enregistrements insérés et ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="3f053-145">The response message contains the number or records inserted and resembles the following:</span></span>  
  
    ```  
    <InsertResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE">  
      <InsertResult>1</InsertResult>  
    </InsertResponse>  
    ```  
  
     <span data-ttu-id="3f053-146">La valeur « 1 » indique qu’un seul enregistrement est inséré dans la table MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="3f053-146">The value “1” denotes that a single record is inserted into the MS_SAMPLE_EMPLOYEE table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f053-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f053-147">See Also</span></span>  
 [<span data-ttu-id="3f053-148">Développer des applications d’Oracle E-Business Suite à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="3f053-148">Develop Oracle E-Business Suite applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)