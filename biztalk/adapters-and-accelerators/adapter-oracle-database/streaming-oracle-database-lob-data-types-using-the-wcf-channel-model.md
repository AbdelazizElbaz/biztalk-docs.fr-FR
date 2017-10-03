---
title: "Diffusion en continu des Types de données LOB de base de données Oracle à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- streaming, Oracle LOB data types
- WCF channel model, streaming Oracle LOB data types
ms.assetid: 513a7cb8-495d-4019-bce1-b5babca3629f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf0ee2f8d1c90f69a206a3006398d52e67f819e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="streaming-oracle-database-lob-data-types-using-the-wcf-channel-model"></a><span data-ttu-id="21cf7-102">Diffusion en continu de base de données LOB Types de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="21cf7-102">Streaming Oracle Database LOB Data Types Using the WCF Channel Model</span></span>
<span data-ttu-id="21cf7-103">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge la diffusion en continu de bout en bout des données LOB pour certaines opérations.</span><span class="sxs-lookup"><span data-stu-id="21cf7-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports end-to-end streaming of LOB data for certain operations.</span></span> <span data-ttu-id="21cf7-104">Les sections de cette rubrique décrivent comment implémenter la diffusion en continu pour les données LOB, lorsque vous utilisez le modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="21cf7-104">The sections in this topic describe how to implement streaming for LOB data when you use the WCF channel model.</span></span>  
  
 <span data-ttu-id="21cf7-105">Pour plus d’informations générales sur la façon dont l’adaptateur prend en charge la diffusion en continu des types de données LOB, consultez [diffusion en continu des types de données dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="21cf7-105">For background information about how the adapter supports streaming of LOB data types, see [Streaming large object data types in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).</span></span> <span data-ttu-id="21cf7-106">Vous devez lire cette rubrique avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="21cf7-106">You should read this topic before proceeding.</span></span>  
  
 <span data-ttu-id="21cf7-107">Un exemple qui montre le flux de données LOB est disponible dans les exemples du Kit de développement logiciel inclus dans le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="21cf7-107">A sample that demonstrates LOB data streaming is available in the SDK samples included with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="21cf7-108">Pour plus d’informations, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).</span><span class="sxs-lookup"><span data-stu-id="21cf7-108">For more information, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="streaming-outbound-messages-to-the-adapter"></a><span data-ttu-id="21cf7-109">Diffusion en continu des Messages sortants à l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="21cf7-109">Streaming Outbound Messages to the Adapter</span></span>  
 <span data-ttu-id="21cf7-110">L’adaptateur prend en charge les données LOB de bout en bout pour le message de demande pour l’opération UpdateLOB de diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="21cf7-110">The adapter supports end-to-end LOB data streaming for the request message for the UpdateLOB operation.</span></span>  
  
 <span data-ttu-id="21cf7-111">Pour prendre en charge la diffusion en continu de bout en bout sur les opérations de UpdateLOB dans le modèle de canal WCF, vous devez :</span><span class="sxs-lookup"><span data-stu-id="21cf7-111">To support end-to-end streaming on UpdateLOB operations in the WCF channel model, you must:</span></span>  
  
1.  <span data-ttu-id="21cf7-112">Définir le **UseAmbientTransaction** liaison de propriété à true.</span><span class="sxs-lookup"><span data-stu-id="21cf7-112">Set the **UseAmbientTransaction** binding property to true.</span></span>  
  
2.  <span data-ttu-id="21cf7-113">Implémentez un **System.ServiceModel.Channels.BodyWriter** qui est capable de diffusion en continu les données LOB (exécution en continu sur les données LOB de valeur de nœud).</span><span class="sxs-lookup"><span data-stu-id="21cf7-113">Implement a **System.ServiceModel.Channels.BodyWriter** that is capable of streaming the LOB data (performing node-value streaming on the LOB data).</span></span>  
  
3.  <span data-ttu-id="21cf7-114">Effectuer l’opération UpdateLOB au sein d’une étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="21cf7-114">Perform the UpdateLOB operation within a transaction scope.</span></span>  
  
4.  <span data-ttu-id="21cf7-115">Créer le **System.ServiceModel.Message** utilisée pour appeler l’opération en fournissant le corps du message avec ce **BodyWriter** à l’aide de la surcharge appropriée de la **Message.Create** (méthode).</span><span class="sxs-lookup"><span data-stu-id="21cf7-115">Create the **System.ServiceModel.Message** used to invoke the operation by supplying the message body with this **BodyWriter** using an appropriate overload of the **Message.Create** method.</span></span>  
  
### <a name="setting-the-useambienttransaction-binding-property"></a><span data-ttu-id="21cf7-116">Définition de la propriété de liaison de UseAmbientTransaction</span><span class="sxs-lookup"><span data-stu-id="21cf7-116">Setting the UseAmbientTransaction Binding Property</span></span>  
 <span data-ttu-id="21cf7-117">L’exemple suivant montre comment créer une liaison pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] et définir le **UseAmbientTransaction** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="21cf7-117">The following example shows how to create a binding for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] and set the **UseAmbientTransaction** binding property.</span></span>  
  
```  
// Create binding  
OracleDBBinding odbBinding = new OracleDBBinding();  
  
//set the binding property  
binding.UseAmbientTransaction = true;  
  
```  
  
### <a name="implementing-a-bodywriter"></a><span data-ttu-id="21cf7-118">Implémentation d’un BodyWriter</span><span class="sxs-lookup"><span data-stu-id="21cf7-118">Implementing a BodyWriter</span></span>  
 <span data-ttu-id="21cf7-119">L’exemple suivant illustre une implémentation d’un **BodyWriter** qui effectue la diffusion en continu de la valeur du nœud.</span><span class="sxs-lookup"><span data-stu-id="21cf7-119">The following example shows an implementation of a **BodyWriter** that performs node-value streaming.</span></span>  
  
```  
/// <summary>  
/// This class overrides the OnWriteBodyContents function to do node-value streaming  
/// </summary>  
class StreamingBodyWriter : BodyWriter, IDisposable  
{  
    XmlReader m_reader = null;  
  
    int m_chunkSize;  
    /// <summary>  
    /// Initializes the body writer  
    /// </summary>  
    /// <param name="reader">Reader for input</param>  
    /// <param name="chunkSize">The chunksize in which the data is passed to adapter</param>  
    public StreamingBodyWriter(XmlReader reader, int chunkSize)  
        : base(false)  
    {  
        m_reader = reader;  
        if (chunkSize \<= 0)  
            throw new ApplicationException("ChunkSize should be a positive value");  
        m_chunkSize = chunkSize;  
    }  
  
    protected override void OnWriteBodyContents(XmlDictionaryWriter writer)  
    {  
        if (m_reader == null)  
            throw new ApplicationException("Reader cannot be null");  
  
        while (m_reader.Read())  
        {  
            switch (m_reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    writer.WriteStartElement(m_reader.LocalName, m_reader.NamespaceURI);  
                    break;  
                case XmlNodeType.Text:  
                    #region Streaming Code  
                    char[] tempBuffer = new char[m_chunkSize];  
                    int length = 0;  
                    while ((length = m_reader.ReadValueChunk(tempBuffer, 0, m_chunkSize)) > 0)  
                    {  
                        writer.WriteString(new String(tempBuffer, 0, length));  
                    }  
                    #endregion  
                    break;  
                case XmlNodeType.EndElement:  
                    writer.WriteEndElement();  
                    break;  
            }  
        }  
  
    }  
  
    #region IDisposable Members  
  
    public void Dispose()  
    {  
        if (m_reader != null)  
        {  
            m_reader.Close();  
            m_reader = null;  
        }  
    }  
  
    #endregion  
}  
```  
  
### <a name="perform-the-operations-within-a-transaction-scope"></a><span data-ttu-id="21cf7-120">Effectuer les opérations au sein d’une étendue de Transaction</span><span class="sxs-lookup"><span data-stu-id="21cf7-120">Perform the Operations Within a Transaction Scope</span></span>  
 <span data-ttu-id="21cf7-121">L’exemple suivant montre comment effectuer des opérations dans une étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="21cf7-121">The following example shows how to perform operations within a transaction scope.</span></span>  
  
```  
// Create a transaction scope  
using(TransactionScope tx = new TransactionScope())  
{  
  // perform operations within the transaction  
  // ...  
  // ...  
  
  //Complete the transaction  
  tx.Complete()  
}  
  
```  
  
### <a name="creating-a-message-by-using-a-bodywriter"></a><span data-ttu-id="21cf7-122">Création d’un Message à l’aide d’un BodyWriter</span><span class="sxs-lookup"><span data-stu-id="21cf7-122">Creating a Message by using a BodyWriter</span></span>  
 <span data-ttu-id="21cf7-123">L’exemple suivant montre comment créer un message de demande de UpdateLOB à l’aide du **BodyWriter** dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="21cf7-123">The following example shows how to create an UpdateLOB request message using the **BodyWriter** in the preceding example.</span></span> <span data-ttu-id="21cf7-124">Les données du message sont lu à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="21cf7-124">The message data is read from a file.</span></span>  
  
```  
// Create a transaction scope  
using(TransactionScope tx = new TransactionScope())  
{  
    XmlReader readerIn = XmlReader.Create ("updatelob.xml");  
    // StreamingBodyWrtier class is responsible for streaming  
    StreamingBodyWriter stBW = new StreamingBodyWriter(readerIn, chunkSize);  
  
    Message InputMsg = Message.CreateMessage(MessageVersion.Default,  
    "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/UpdateLOB",   
    stBW);  
  
    //Send the request message and get the output message  
    OutputMsg = channel.Request(InputMsg);  
  
    tx.Complete();  
}  
  
```  
  
## <a name="streaming-inbound-messages-from-the-adapter"></a><span data-ttu-id="21cf7-125">Diffusion en continu les Messages entrants à partir de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="21cf7-125">Streaming Inbound Messages from the Adapter</span></span>  
 <span data-ttu-id="21cf7-126">L’adaptateur prend en charge les données LOB de bout en bout de diffusion en continu pour les messages entrants suivants :</span><span class="sxs-lookup"><span data-stu-id="21cf7-126">The adapter supports end-to-end LOB data streaming for the following inbound messages:</span></span>  
  
-   <span data-ttu-id="21cf7-127">Message de réponse pour les fonctions out ou IN OUT qui contiennent des données LOB.</span><span class="sxs-lookup"><span data-stu-id="21cf7-127">Response message for functions with OUT or IN OUT parameters that contain LOB data.</span></span> <span data-ttu-id="21cf7-128">Notez que les paramètres de TYPE d’enregistrement peuvent contenir des colonnes de données LOB.</span><span class="sxs-lookup"><span data-stu-id="21cf7-128">Note that RECORD TYPE parameters can contain LOB data columns.</span></span>  
  
-   <span data-ttu-id="21cf7-129">Message de réponse pour les fonctions avec des paramètres OUT REF CURSOR (ou valeurs de retour) qui contiennent des données LOB.</span><span class="sxs-lookup"><span data-stu-id="21cf7-129">Response message for functions with OUT REF CURSOR parameters (or return values) that contain LOB data.</span></span> <span data-ttu-id="21cf7-130">Cela inclut le côté de la sortie de paramètres dans des REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="21cf7-130">This includes the output side of IN OUT REF CURSOR parameters.</span></span>  
  
-   <span data-ttu-id="21cf7-131">Message de réponse pour les procédures avec IN ou dans les paramètres qui contiennent des données LOB.</span><span class="sxs-lookup"><span data-stu-id="21cf7-131">Response message for procedures with IN or IN OUT parameters that contain LOB data.</span></span> <span data-ttu-id="21cf7-132">Notez que les paramètres de TYPE d’enregistrement peuvent contenir des colonnes de données LOB.</span><span class="sxs-lookup"><span data-stu-id="21cf7-132">Note that RECORD TYPE parameters can contain LOB data columns.</span></span>  
  
-   <span data-ttu-id="21cf7-133">Message de réponse pour les procédures avec les paramètres de sortie REF CURSOR qui contiennent des données LOB.</span><span class="sxs-lookup"><span data-stu-id="21cf7-133">Response message for procedures with OUT REF CURSOR parameters that contain LOB data.</span></span> <span data-ttu-id="21cf7-134">Cela inclut le côté de la sortie de paramètres dans des REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="21cf7-134">This includes the output side of IN OUT REF CURSOR parameters</span></span>  
  
-   <span data-ttu-id="21cf7-135">Message de réponse pour les opérations de SQLEXECUTE qui retournent des jeux de résultats qui contiennent des données LOB.</span><span class="sxs-lookup"><span data-stu-id="21cf7-135">Response message for SQLEXECUTE operations that return result sets that contain LOB data.</span></span>  
  
-   <span data-ttu-id="21cf7-136">Message de réponse pour la Table ou la vue des opérations Select qui retournent des données LOB dans le résultat est définie.</span><span class="sxs-lookup"><span data-stu-id="21cf7-136">Response message for Table or view Select operations that return LOB data in the result set.</span></span>  
  
-   <span data-ttu-id="21cf7-137">Message de demande pour l’opération POLLINGSTMT (entrante)</span><span class="sxs-lookup"><span data-stu-id="21cf7-137">Request message for the (inbound) POLLINGSTMT operation</span></span>  
  
 <span data-ttu-id="21cf7-138">Pour prendre en charge la diffusion en continu de bout en bout sur un message entrant dans le modèle de canal WCF, vous devez :</span><span class="sxs-lookup"><span data-stu-id="21cf7-138">To support end-to-end streaming on an inbound message in the WCF channel model, you must:</span></span>  
  
1.  <span data-ttu-id="21cf7-139">Implémentez un **System.Xml.XmlDictionaryWriter** qui est capable de diffusion en continu les données LOB (exécution en continu sur les données LOB de valeur de nœud).</span><span class="sxs-lookup"><span data-stu-id="21cf7-139">Implement a **System.Xml.XmlDictionaryWriter** that is capable of streaming the LOB data (performing node-value streaming on the LOB data).</span></span>  
  
2.  <span data-ttu-id="21cf7-140">Consommer le **Message** en appelant **WriteBodyContents** méthode avec cette **XmlDictionaryWriter**.</span><span class="sxs-lookup"><span data-stu-id="21cf7-140">Consume the **Message** by invoking **WriteBodyContents** method with this **XmlDictionaryWriter**.</span></span>  
  
### <a name="implementing-an-xmldictionarywriter"></a><span data-ttu-id="21cf7-141">Implémentation de XmlDictionaryWriter</span><span class="sxs-lookup"><span data-stu-id="21cf7-141">Implementing an XmlDictionaryWriter</span></span>  
 <span data-ttu-id="21cf7-142">L’exemple suivant illustre une implémentation d’un **XmlDictionaryWriter** qui effectue la diffusion en continu de la valeur du nœud.</span><span class="sxs-lookup"><span data-stu-id="21cf7-142">The following example shows an implementation of an **XmlDictionaryWriter** that performs node-value streaming.</span></span>  
  
```  
using System;  
using System.Xml;  
using System.Text;  
  
class FileXmlWriter : XmlDictionaryWriter  
{  
    XmlTextWriter xts;  
  
    public FileXmlWriter(string file)  
    {  
        xts = new XmlTextWriter(file, Encoding.UTF8);  
    }  
  
    public override void WriteBase64(byte[] buffer, int index, int count)  
    {  
        xts.WriteBase64(buffer, index, count);  
    }  
  
    public override void WriteCData(string text)  
    {  
        xts.WriteCData(text);  
    }  
  
    public override void WriteCharEntity(char ch)  
    {  
        xts.WriteCharEntity(ch);  
    }  
  
    public override void WriteChars(char[] buffer, int index, int count)  
    {  
        xts.WriteChars(buffer, index, count);  
    }  
  
    public override void WriteComment(string text)  
    {  
        xts.WriteComment(text);  
    }  
  
    public override void WriteDocType(string name, string pubid, string sysid, string subset)  
    {  
        xts.WriteDocType(name, pubid, sysid, subset);  
    }  
  
    public override void WriteEndAttribute()  
    {  
        xts.WriteEndAttribute();  
    }  
  
    public override void WriteEndDocument()  
    {  
        xts.WriteEndDocument();  
    }  
  
    public override void WriteEndElement()  
    {  
        xts.WriteEndElement();  
    }  
  
    public override void WriteEntityRef(string name)  
    {  
        xts.WriteEntityRef(name);  
    }  
  
    public override void WriteFullEndElement()  
    {  
        xts.WriteFullEndElement();  
    }  
  
    public override void WriteProcessingInstruction(string name, string text)  
    {  
        xts.WriteProcessingInstruction(name, text);  
    }  
  
    public override void WriteRaw(string data)  
    {  
        xts.WriteRaw(data);  
    }  
  
    public override void WriteRaw(char[] buffer, int index, int count)  
    {  
        xts.WriteRaw(buffer, index, count);  
    }  
  
    public override void WriteStartAttribute(string prefix, string localName, string ns)  
    {  
        xts.WriteStartAttribute(prefix, localName, ns);  
    }  
  
    public override void WriteStartDocument(bool standalone)  
    {  
        xts.WriteStartDocument(standalone);  
    }  
  
    public override void WriteStartDocument()  
    {  
        xts.WriteStartDocument();  
    }  
  
    public override void WriteStartElement(string prefix, string localName, string ns)  
    {  
        xts.WriteStartElement(localName);  
    }  
  
    public override void WriteString(string text)  
    {  
        xts.WriteString(text);  
    }  
  
    public override void WriteSurrogateCharEntity(char lowChar, char highChar)  
    {  
        xts.WriteSurrogateCharEntity(lowChar, highChar);  
    }  
  
    public override void WriteWhitespace(string ws)  
    {  
        xts.WriteWhitespace(ws);  
    }  
  
    public override void Close()  
    {  
        xts.Close();  
    }  
  
    public override void Flush()  
    {  
        xts.Flush();  
    }  
  
    public override string LookupPrefix(string ns)  
    {  
        return xts.LookupPrefix(ns);  
    }  
  
    public override WriteState WriteState  
    {  
        get { return xts.WriteState; }  
    }  
  
}  
```  
  
### <a name="consuming-a-message-by-using-an-xmldictionarywriter"></a><span data-ttu-id="21cf7-143">Consommation d’un Message à l’aide du XmlDictionaryWriter</span><span class="sxs-lookup"><span data-stu-id="21cf7-143">Consuming a Message by using an XmlDictionaryWriter</span></span>  
 <span data-ttu-id="21cf7-144">L’exemple suivant montre comment utiliser un message de réponse Select de table à l’aide du **FileXmlWriter** implémentée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="21cf7-144">The following example shows how to consume a table Select response message using the **FileXmlWriter** implemented in the preceding example.</span></span> <span data-ttu-id="21cf7-145">(Le **FileWriter** classe a été créé en définissant une sous-classe **XmlDictionaryWriter**.) L’exemple utilise un **IRequestChannel** canal pour appeler l’opération Select.</span><span class="sxs-lookup"><span data-stu-id="21cf7-145">(The **FileWriter** class was created by sub-classing **XmlDictionaryWriter**.) The example uses an **IRequestChannel** channel to invoke the Select operation.</span></span> <span data-ttu-id="21cf7-146">Les détails de la création du canal ont été omis.</span><span class="sxs-lookup"><span data-stu-id="21cf7-146">The details of the channel creation have been omitted.</span></span> <span data-ttu-id="21cf7-147">Le message de requête de sélection est lu à partir d’un fichier et le message de réponse Select est écrite dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="21cf7-147">The Select request message is read from a file and the Select response message is written to a file.</span></span>  
  
```  
// Read Select message body from a file  
XmlReader readerIn = XmlReader.Create("select.xml");  
Message InputMsg = Message.CreateMessage(MessageVersion.Default,  
    "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/Select", readerIn);  
  
Message OutputMsg = channel.Request(InputMsg);  
  
// Streaming response message to select_output.xml using the custom XmlDictionaryWriter;  
FileXmlWriter fileXmlWriter = new FileXmlWriter("select_output.xml");  
OutputMsg.WriteBodyContents(fileXmlWriter);  
fileXmlWriter.Flush();  
fileXmlWriter.Close();  
  
// Streaming complete close output message;  
OutputMsg.Close();  
```  
  
 <span data-ttu-id="21cf7-148">Le code XML suivant montre le message de demande (contenu du fichier select.xml) pour l’opération de sélection.</span><span class="sxs-lookup"><span data-stu-id="21cf7-148">The following XML shows the request message (contents of the select.xml file) for the Select operation.</span></span> <span data-ttu-id="21cf7-149">La table CUSTOMER contient une colonne BLOB nommée PHOTO.</span><span class="sxs-lookup"><span data-stu-id="21cf7-149">The CUSTOMER table contains a BLOB column named PHOTO.</span></span>  
  
```  
<Select xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER">  
  <COLUMN_NAMES>*</COLUMN_NAMES>  
  <FILTER>NAME='Kim Ralls'</FILTER>  
</Select>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21cf7-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21cf7-150">See Also</span></span>  
 [<span data-ttu-id="21cf7-151">Développer des applications de base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="21cf7-151">Develop Oracle Database applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)