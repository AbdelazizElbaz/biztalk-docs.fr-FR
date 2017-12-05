---
title: "Exécuter une opération d’insertion dans la base de données Oracle à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inserting data, using a channel
- WCF channel model, performing an Insert operation
- how to, perform an insert operation using a channel
- channel programming, performing an insert operation
- performing an insert operation, using a channel
ms.assetid: 85c44507-0166-42ef-a908-6098f7a683fc
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fd689cbf378f41578c5f46b3067410a184cf650
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model"></a><span data-ttu-id="2d458-102">Exécuter une opération d’insertion dans la base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="2d458-102">Run an Insert Operation in Oracle Database using the WCF Channel Model</span></span>
<span data-ttu-id="2d458-103">Cette section montre comment insérer un enregistrement dans une base de données Oracle à l’aide d’un canal.</span><span class="sxs-lookup"><span data-stu-id="2d458-103">This section shows how to insert a record into an Oracle database by using a channel.</span></span> <span data-ttu-id="2d458-104">Lorsque vous envoyez un message, vous devez spécifier un corps de message et une action de message.</span><span class="sxs-lookup"><span data-stu-id="2d458-104">You must specify both a message body and a message action when you send a message.</span></span>  
  
## <a name="the-insert-message"></a><span data-ttu-id="2d458-105">Le Message d’insertion</span><span class="sxs-lookup"><span data-stu-id="2d458-105">The Insert Message</span></span>  
 <span data-ttu-id="2d458-106">Le code XML suivant montre un corps de message pour une opération d’insertion sur les ressources humaines. Table des employés.</span><span class="sxs-lookup"><span data-stu-id="2d458-106">The following XML shows a message body for an Insert operation on the HR.EMPLOYEES table.</span></span> <span data-ttu-id="2d458-107">Le jeu d’enregistrements se compose d’un enregistrement d’employé unique.</span><span class="sxs-lookup"><span data-stu-id="2d458-107">The record set consists of a single employee record.</span></span> <span data-ttu-id="2d458-108">Pour plus d’informations sur le schéma d’un message d’insertion, consultez [des schémas de Message pour la base opérations d’insertion, mise à jour, supprimer et sélectionnez sur les Tables et vues](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).</span><span class="sxs-lookup"><span data-stu-id="2d458-108">For more information about the schema of an Insert message, see [Message Schemas for the Basic Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).</span></span> <span data-ttu-id="2d458-109">Voici le contenu du fichier Employee_Insert.xml utilisé dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="2d458-109">This is the contents of the Employee_Insert.xml file used in the example.</span></span>  
  
```  
<!-- New namespace: http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEES -->  
<Insert xmlns="http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEES">  
    <RECORDSET xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
        <EMPLOYEESRECORDINSERT>  
            <EMPLOYEE_ID>0</EMPLOYEE_ID>  
            <FIRST_NAME>Anton</FIRST_NAME>  
            <LAST_NAME>Kirilov</LAST_NAME>  
            <EMAIL></EMAIL>  
            <PHONE_NUMBER>555-0198</PHONE_NUMBER>  
            <HIRE_DATE>2007-03-01T00:00:00.0000000</HIRE_DATE>  
            <JOB_ID>FI_ACCOUNT</JOB_ID>  
            <SALARY>5000</SALARY>  
            <COMMISSION_PCT>0.15</COMMISSION_PCT>  
            <MANAGER_ID>108</MANAGER_ID>  
            <DEPARTMENT_ID>100</DEPARTMENT_ID>  
       </EMPLOYEESRECORDINSERT>  
    </RECORDSET>  
</Insert>  
```  
  
## <a name="specifying-the-message-action"></a><span data-ttu-id="2d458-110">Spécification de l’Action du Message</span><span class="sxs-lookup"><span data-stu-id="2d458-110">Specifying the Message Action</span></span>  
 <span data-ttu-id="2d458-111">Vous devez spécifier une action de message lorsque vous envoyez un message SOAP à le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d458-111">You must specify a message action when you send a SOAP message to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="2d458-112">Vous pouvez spécifier l’action du message lorsque vous créez le message comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2d458-112">You can specify the message action when you create the message as in the following example.</span></span>  
  
```  
Message messageIn2 = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEES/Insert", readerIn2);  
```  
  
 <span data-ttu-id="2d458-113">L’action du message dans cet exemple, « / HR, Table ou employés/Insert », spécifie qu’une opération d’insertion sur les ressources humaines. Table employés doit être effectuée</span><span class="sxs-lookup"><span data-stu-id="2d458-113">The message action in this example, "/HR/Table/EMPLOYEES/Insert", specifies that an Insert operation on the HR.EMPLOYEES table is to be performed</span></span>  
  
## <a name="sending-the-insert-message"></a><span data-ttu-id="2d458-114">Envoi du Message d’insertion</span><span class="sxs-lookup"><span data-stu-id="2d458-114">Sending the Insert Message</span></span>  
 <span data-ttu-id="2d458-115">Cet exemple montre comment effectuer une opération d’insertion sur une table Oracle sur un canal.</span><span class="sxs-lookup"><span data-stu-id="2d458-115">This example shows how to perform an Insert operation on an Oracle table over a channel.</span></span> <span data-ttu-id="2d458-116">Le code utilise l’opération SQLEXECUTE exposée par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour retourner la valeur suivante d’une séquence Oracle.</span><span class="sxs-lookup"><span data-stu-id="2d458-116">The code uses the SQLEXECUTE operation exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to return the next value of an Oracle SEQUENCE.</span></span> <span data-ttu-id="2d458-117">Cette valeur est ensuite écrites dans le champ EMPLOYEE_ID dans l’enregistrement de l’insertion.</span><span class="sxs-lookup"><span data-stu-id="2d458-117">This value is then written to the EMPLOYEE_ID field in the Insert record.</span></span> <span data-ttu-id="2d458-118">Ce modèle vous permet d’insérer des lignes dans les bases de données qui ont une valeur de clé primaire générée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="2d458-118">This pattern enables you to insert rows into databases that have an auto-generated primary key value.</span></span> <span data-ttu-id="2d458-119">Pour plus d’informations sur l’appel de l’opération SQLEXECUTE via un canal, consultez [exécuter une opération SQLEXECUTE en utilisant le modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md).</span><span class="sxs-lookup"><span data-stu-id="2d458-119">For more information about invoking the SQLEXECUTE operation over a channel, see [Run a SQLEXECUTE Operation by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md).</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Xml;  
using System.IO;  
  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
  
using Microsoft.ServiceModel.Adapters;  
using Microsoft.Adapters.OracleDB;  
  
namespace OracleDMLChannel  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Create Endpoint  
            EndpointAddress address = new EndpointAddress("oracledb://ADAPTER");  
  
            // Create Binding  
            OracleDBBinding binding = new OracleDBBinding();  
  
            // Create Channel Factory  
            ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
            factory.Credentials.UserName.UserName = "HR";  
            factory.Credentials.UserName.Password = "TIGER";  
            factory.Open();  
  
            // Create Request Channel  
            IRequestChannel channel = factory.CreateChannel();  
            channel.Open();  
  
            // Send Request  
            System.Xml.XmlReader readerIn = System.Xml.XmlReader.Create("SQLExecute.xml");  
  
            Message messageIn = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE", readerIn);  
            Message messageOut = channel.Request(messageIn);  
  
            // Get Response XML  
            XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
  
            // Get Employee ID  
            string id = null;  
            XmlDocument doc = new XmlDocument();  
            doc.Load(readerOut);  
            XmlNodeList list = doc.GetElementsByTagName("ColumnValue");  
            if (list.Count > 0) id = list[0].InnerXml;  
  
            // Compose Insert XML  
            XmlDocument insertDoc = new XmlDocument();  
            insertDoc.Load("Employee_Insert.xml");  
  
            // Change Employee ID  
            XmlNodeList empidList = insertDoc.GetElementsByTagName("EMPLOYEE_ID");  
            XmlNode empidNode = empidList[0];  
            empidNode.InnerXml = id;  
  
            // Change email  
            XmlNodeList emailList = insertDoc.GetElementsByTagName("EMAIL");  
            XmlNode emailNode = emailList[0];  
            emailNode.InnerXml = "scotty" + id + "@microsoft.com";  
  
            // Change date  
            XmlNodeList dateList = insertDoc.GetElementsByTagName("HIRE_DATE");  
            XmlNode dateNode = dateList[0];  
            dateNode.InnerXml = "2007-03-01T00:00:00.0000000";  
  
            StringReader strReader = new StringReader(insertDoc.InnerXml);  
            XmlReader readerIn2 = XmlReader.Create(strReader);  
  
            // Send XML  
            Message messageIn2 = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEES/Insert ", readerIn2);  
            Message messageOut2 = channel.Request(messageIn2);  
  
            // Close the messages  
            messageOut.Close();  
            messageOut2.Close();  
  
            channel.Close();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d458-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d458-120">See Also</span></span>  
 <span data-ttu-id="2d458-121">[Développer des applications de base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md) </span><span class="sxs-lookup"><span data-stu-id="2d458-121">[Develop Oracle Database applications Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md) </span></span>  
 <span data-ttu-id="2d458-122">[Créer un canal à l’aide de la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md) </span><span class="sxs-lookup"><span data-stu-id="2d458-122">[Create a channel using Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md) </span></span>  
 <span data-ttu-id="2d458-123">[Exécuter une opération SQLEXECUTE en utilisant le modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md) </span><span class="sxs-lookup"><span data-stu-id="2d458-123">[Run a SQLEXECUTE Operation by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md) </span></span>  
 [<span data-ttu-id="2d458-124">Appeler une fonction dans la base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="2d458-124">Invoke a Function in Oracle Database Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)