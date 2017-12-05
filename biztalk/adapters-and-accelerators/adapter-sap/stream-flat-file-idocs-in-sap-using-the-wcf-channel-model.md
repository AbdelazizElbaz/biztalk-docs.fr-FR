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
ms.openlocfilehash: c8de850022a03a3be0310da3022a2cf496c94f30
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="stream-flat-file-idocs-in-sap-using-the-wcf-channel-model"></a>Flux de fichier plat les IDOC dans SAP à l’aide du modèle de canal WCF
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] prend en charge la diffusion en continu pour les opérations SendIdoc et ReceiveIdoc-valeur du nœud. Ces opérations sont utilisées pour envoyer et recevoir (string) IDOC vers et à partir de l’adaptateur de fichier plat. Dans ces deux opérations, les données pour l’IDOC entière sont contenues dans une chaîne sous un seul nœud (\<idocData\>). Des IDOC volumineux, la diffusion en continu les données IDOC entre l’adaptateur et votre code peut enregistrer les ressources de mémoire importante.  
  
 Pour plus d’informations générales sur la façon dont l’adaptateur prend en charge la diffusion en continu, consultez [l’adaptateur SAP et diffusion en continu](../../adapters-and-accelerators/adapter-sap/streaming-and-the-sap-adapter.md). Vous devez lire cette rubrique avant de continuer.  
  
 Les sections de cette rubrique décrivent comment implémenter la valeur du nœud de diffusion en continu pour les opérations SendIdoc et ReceiveIdoc lorsque vous utilisez le modèle de canal WCF.  
  
## <a name="streaming-outbound-flat-file-idocs-to-the-adapter"></a>Diffusion en continu IDOC de fichier plat sortants à la carte  
 L’adaptateur prend en charge la diffusion en continu sur le message de demande pour l’opération SendIdoc-valeur du nœud.  
  
 Pour prendre en charge la diffusion en continu sur les opérations de SendIdoc dans le modèle de canal WCF de valeur de nœud, vous devez :  
  
1.  Implémentez un **System.ServiceModel.Channels.BodyWriter** qui est capable de diffusion en continu les données IDOC (exécution la valeur du nœud de diffusion en continu sur les données IDOC).  
  
2.  Créer le **System.ServiceModel.Message** utilisée pour appeler l’opération en fournissant le corps du message avec ce **BodyWriter** à l’aide de la surcharge appropriée de la **Message.Create** (méthode).  
  
### <a name="implementing-a-bodywriter"></a>Implémentation d’un BodyWriter  
 L’exemple suivant illustre une implémentation d’un **BodyWriter** qui effectue la diffusion en continu de la valeur du nœud.  
  
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
  
### <a name="creating-a-message-by-using-a-bodywriter"></a>Création d’un Message à l’aide d’un BodyWriter  
 L’exemple suivant montre comment créer un message de demande de SendIdoc à l’aide du **BodyWriter** dans l’exemple précédent. Les données du message sont lu à partir d’un fichier.  
  
```  
XmlReader readerIn = XmlReader.Create ("sendidoc.xml");  
// StreamingBodyWrtier class is responsible for streaming  
StreamingBodyWriter stBW = new StreamingBodyWriter(readerIn, chunkSize);  
  
Message InputMsg = Message.CreateMessage(MessageVersion.Default,  
    "http://Microsoft.LobServices.SAP/2007/03/Idoc/SendIdoc",   
    stBW);  
  
```  
  
## <a name="streaming-inbound-flat-file-idocs-from-the-adapter"></a>Diffusion en continu IDOC de fichier plat entrants à partir de l’adaptateur  
 Vous recevez un IDOC de fichier plat dans l’opération ReceiveIdoc entrante. L’adaptateur prend en charge la diffusion en continu sur le message de demande pour l’opération ReceiveIdoc-valeur du nœud.  
  
 Pour prendre en charge la diffusion en continu sur les opérations de ReceiveIdoc dans le modèle de canal WCF de valeur de nœud, vous devez :  
  
1.  Implémentez un **System.Xml.XmlDictionaryWriter** qui est capable de diffusion en continu les données IDOC (exécution la valeur du nœud de diffusion en continu sur les données IDOC).  
  
2.  Consommer le **Message** en appelant son **WriteBodyContents** méthode avec cette **XmlDictionaryWriter**.  
  
### <a name="implementing-an-xmldictionarywriter"></a>Implémentation de XmlDictionaryWriter  
 L’exemple suivant illustre une implémentation d’un **XmlDictionaryWriter** qui effectue la diffusion en continu de la valeur du nœud.  
  
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
  
### <a name="consuming-a-message-by-using-an-xmldictionarywriter"></a>Consommation d’un Message à l’aide du XmlDictionaryWriter  
 L’exemple suivant montre comment utiliser un message de demande de ReceiveIdoc à l’aide du **FileXmlWriter** implémentée dans l’exemple précédent. (Le **FileWriter** classe a été créé en définissant une sous-classe **XmlDictionaryWriter**.) L’exemple utilise un **IReplyChannel** doit recevoir l’opération ReceiveIdoc. Les détails de la création du canal ont été omis. Le message de demande ReceiveIdoc est écrit dans un fichier.  
  
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
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications en utilisant le modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)