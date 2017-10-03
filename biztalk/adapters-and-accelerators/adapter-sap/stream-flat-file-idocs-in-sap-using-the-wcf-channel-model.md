---
title: "Flux de fichier plat les IDOC dans SAP à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF channel model, streaming flat-file IDOCs
ms.assetid: 5010e215-d8d0-47c8-93a6-20cfdeff2951
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3d9641f894a493aa5c2c298a71b1b5a49ffb55a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="stream-flat-file-idocs-in-sap-using-the-wcf-channel-model"></a><span data-ttu-id="54020-102">Flux de fichier plat les IDOC dans SAP à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="54020-102">Stream Flat-File IDOCs in SAP using the WCF Channel Model</span></span>
<span data-ttu-id="54020-103">Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] prend en charge la diffusion en continu pour les opérations SendIdoc et ReceiveIdoc-valeur du nœud.</span><span class="sxs-lookup"><span data-stu-id="54020-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports node-value streaming for the SendIdoc and ReceiveIdoc operations.</span></span> <span data-ttu-id="54020-104">Ces opérations sont utilisées pour envoyer et recevoir (string) IDOC vers et à partir de l’adaptateur de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="54020-104">These operations are used to send and receive flat-file (string) IDOCs to and from the adapter.</span></span> <span data-ttu-id="54020-105">Dans ces deux opérations, les données pour l’IDOC entière sont contenues dans une chaîne sous un seul nœud (\<idocData >).</span><span class="sxs-lookup"><span data-stu-id="54020-105">In both of these operations, the data for the entire IDOC is contained in a string under a single node (\<idocData>).</span></span> <span data-ttu-id="54020-106">Des IDOC volumineux, la diffusion en continu les données IDOC entre l’adaptateur et votre code peut enregistrer les ressources de mémoire importante.</span><span class="sxs-lookup"><span data-stu-id="54020-106">For large IDOCs, streaming the IDOC data between the adapter and your code may save significant memory resources.</span></span>  
  
 <span data-ttu-id="54020-107">Pour plus d’informations générales sur la façon dont l’adaptateur prend en charge la diffusion en continu, consultez [l’adaptateur SAP et diffusion en continu](../../adapters-and-accelerators/adapter-sap/streaming-and-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="54020-107">For background information about how the adapter supports streaming, see [Streaming and the SAP Adapter](../../adapters-and-accelerators/adapter-sap/streaming-and-the-sap-adapter.md).</span></span> <span data-ttu-id="54020-108">Vous devez lire cette rubrique avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="54020-108">You should read this topic before proceeding.</span></span>  
  
 <span data-ttu-id="54020-109">Les sections de cette rubrique décrivent comment implémenter la valeur du nœud de diffusion en continu pour les opérations SendIdoc et ReceiveIdoc lorsque vous utilisez le modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="54020-109">The sections in this topic describe how to implement node-value streaming for the SendIdoc and ReceiveIdoc operations when you use the WCF channel model.</span></span>  
  
## <a name="streaming-outbound-flat-file-idocs-to-the-adapter"></a><span data-ttu-id="54020-110">Diffusion en continu IDOC de fichier plat sortants à la carte</span><span class="sxs-lookup"><span data-stu-id="54020-110">Streaming Outbound Flat-File IDOCs to the Adapter</span></span>  
 <span data-ttu-id="54020-111">L’adaptateur prend en charge la diffusion en continu sur le message de demande pour l’opération SendIdoc-valeur du nœud.</span><span class="sxs-lookup"><span data-stu-id="54020-111">The adapter supports node-value streaming on the request message for the SendIdoc operation.</span></span>  
  
 <span data-ttu-id="54020-112">Pour prendre en charge la diffusion en continu sur les opérations de SendIdoc dans le modèle de canal WCF de valeur de nœud, vous devez :</span><span class="sxs-lookup"><span data-stu-id="54020-112">To support node-value streaming on SendIdoc operations in the WCF channel model, you must:</span></span>  
  
1.  <span data-ttu-id="54020-113">Implémentez un **System.ServiceModel.Channels.BodyWriter** qui est capable de diffusion en continu les données IDOC (exécution la valeur du nœud de diffusion en continu sur les données IDOC).</span><span class="sxs-lookup"><span data-stu-id="54020-113">Implement a **System.ServiceModel.Channels.BodyWriter** that is capable of streaming the IDOC data (performing node-value streaming on the IDOC data).</span></span>  
  
2.  <span data-ttu-id="54020-114">Créer le **System.ServiceModel.Message** utilisée pour appeler l’opération en fournissant le corps du message avec ce **BodyWriter** à l’aide de la surcharge appropriée de la **Message.Create** (méthode).</span><span class="sxs-lookup"><span data-stu-id="54020-114">Create the **System.ServiceModel.Message** used to invoke the operation by supplying the message body with this **BodyWriter** using an appropriate overload of the **Message.Create** method.</span></span>  
  
### <a name="implementing-a-bodywriter"></a><span data-ttu-id="54020-115">Implémentation d’un BodyWriter</span><span class="sxs-lookup"><span data-stu-id="54020-115">Implementing a BodyWriter</span></span>  
 <span data-ttu-id="54020-116">L’exemple suivant illustre une implémentation d’un **BodyWriter** qui effectue la diffusion en continu de la valeur du nœud.</span><span class="sxs-lookup"><span data-stu-id="54020-116">The following example shows an implementation of a **BodyWriter** that performs node-value streaming.</span></span>  
  
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
        if (chunkSize <= 0)  
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
  
### <a name="creating-a-message-by-using-a-bodywriter"></a><span data-ttu-id="54020-117">Création d’un Message à l’aide d’un BodyWriter</span><span class="sxs-lookup"><span data-stu-id="54020-117">Creating a Message by using a BodyWriter</span></span>  
 <span data-ttu-id="54020-118">L’exemple suivant montre comment créer un message de demande de SendIdoc à l’aide du **BodyWriter** dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="54020-118">The following example shows how to create a SendIdoc request message using the **BodyWriter** in the preceding example.</span></span> <span data-ttu-id="54020-119">Les données du message sont lu à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="54020-119">The message data is read from a file.</span></span>  
  
```  
XmlReader readerIn = XmlReader.Create ("sendidoc.xml");  
// StreamingBodyWrtier class is responsible for streaming  
StreamingBodyWriter stBW = new StreamingBodyWriter(readerIn, chunkSize);  
  
Message InputMsg = Message.CreateMessage(MessageVersion.Default,  
    "http://Microsoft.LobServices.SAP/2007/03/Idoc/SendIdoc",   
    stBW);  
  
```  
  
## <a name="streaming-inbound-flat-file-idocs-from-the-adapter"></a><span data-ttu-id="54020-120">Diffusion en continu IDOC de fichier plat entrants à partir de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="54020-120">Streaming Inbound Flat-File IDOCs from the Adapter</span></span>  
 <span data-ttu-id="54020-121">Vous recevez un IDOC de fichier plat dans l’opération ReceiveIdoc entrante.</span><span class="sxs-lookup"><span data-stu-id="54020-121">You receive a flat-file IDOCs in the inbound ReceiveIdoc operation.</span></span> <span data-ttu-id="54020-122">L’adaptateur prend en charge la diffusion en continu sur le message de demande pour l’opération ReceiveIdoc-valeur du nœud.</span><span class="sxs-lookup"><span data-stu-id="54020-122">The adapter supports node-value streaming on the request message for the ReceiveIdoc operation.</span></span>  
  
 <span data-ttu-id="54020-123">Pour prendre en charge la diffusion en continu sur les opérations de ReceiveIdoc dans le modèle de canal WCF de valeur de nœud, vous devez :</span><span class="sxs-lookup"><span data-stu-id="54020-123">To support node-value streaming on ReceiveIdoc operations in the WCF channel model, you must:</span></span>  
  
1.  <span data-ttu-id="54020-124">Implémentez un **System.Xml.XmlDictionaryWriter** qui est capable de diffusion en continu les données IDOC (exécution la valeur du nœud de diffusion en continu sur les données IDOC).</span><span class="sxs-lookup"><span data-stu-id="54020-124">Implement a **System.Xml.XmlDictionaryWriter** that is capable of streaming the IDOC data (performing node-value streaming on the IDOC data).</span></span>  
  
2.  <span data-ttu-id="54020-125">Consommer le **Message** en appelant son **WriteBodyContents** méthode avec cette **XmlDictionaryWriter**.</span><span class="sxs-lookup"><span data-stu-id="54020-125">Consume the **Message** by invoking its **WriteBodyContents** method with this **XmlDictionaryWriter**.</span></span>  
  
### <a name="implementing-an-xmldictionarywriter"></a><span data-ttu-id="54020-126">Implémentation de XmlDictionaryWriter</span><span class="sxs-lookup"><span data-stu-id="54020-126">Implementing an XmlDictionaryWriter</span></span>  
 <span data-ttu-id="54020-127">L’exemple suivant illustre une implémentation d’un **XmlDictionaryWriter** qui effectue la diffusion en continu de la valeur du nœud.</span><span class="sxs-lookup"><span data-stu-id="54020-127">The following example shows an implementation of an **XmlDictionaryWriter** that performs node-value streaming.</span></span>  
  
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
  
### <a name="consuming-a-message-by-using-an-xmldictionarywriter"></a><span data-ttu-id="54020-128">Consommation d’un Message à l’aide du XmlDictionaryWriter</span><span class="sxs-lookup"><span data-stu-id="54020-128">Consuming a Message by Using an XmlDictionaryWriter</span></span>  
 <span data-ttu-id="54020-129">L’exemple suivant montre comment utiliser un message de demande de ReceiveIdoc à l’aide du **FileXmlWriter** implémentée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="54020-129">The following example shows how to consume a ReceiveIdoc request message using the **FileXmlWriter** implemented in the preceding example.</span></span> <span data-ttu-id="54020-130">(Le **FileWriter** classe a été créé en définissant une sous-classe **XmlDictionaryWriter**.) L’exemple utilise un **IReplyChannel** doit recevoir l’opération ReceiveIdoc.</span><span class="sxs-lookup"><span data-stu-id="54020-130">(The **FileWriter** class was created by sub-classing **XmlDictionaryWriter**.) The example uses an **IReplyChannel** channel to receive the ReceiveIdoc operation.</span></span> <span data-ttu-id="54020-131">Les détails de la création du canal ont été omis.</span><span class="sxs-lookup"><span data-stu-id="54020-131">The details of the channel creation have been omitted.</span></span> <span data-ttu-id="54020-132">Le message de demande ReceiveIdoc est écrit dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="54020-132">The ReceiveIdoc request message is written to a file.</span></span>  
  
```  
// Receive the ReceiveIdoc request message from the adapter.  
RequestContext rc = channel.ReceiveRequest();  
Message inputMsg = rc.RequestMessage;  
  
// Stream the request message to received_idoc.xml using the custom XmlDictionaryWriter.  
FileXmlWriter fileXmlWriter = new FileXmlWriter("received_idoc.xml");  
inputMsg.WriteBodyContents(fileXmlWriter);  
fileXmlWriter.Flush();  
fileXmlWriter.Close();  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="54020-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54020-133">See Also</span></span>  
[<span data-ttu-id="54020-134">Développer des applications à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="54020-134">Develop applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)