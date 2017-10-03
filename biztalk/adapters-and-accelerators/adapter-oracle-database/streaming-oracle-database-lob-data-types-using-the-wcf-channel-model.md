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
# <a name="streaming-oracle-database-lob-data-types-using-the-wcf-channel-model"></a>Diffusion en continu de base de données LOB Types de données Oracle à l’aide du modèle de canal WCF
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge la diffusion en continu de bout en bout des données LOB pour certaines opérations. Les sections de cette rubrique décrivent comment implémenter la diffusion en continu pour les données LOB, lorsque vous utilisez le modèle de canal WCF.  
  
 Pour plus d’informations générales sur la façon dont l’adaptateur prend en charge la diffusion en continu des types de données LOB, consultez [diffusion en continu des types de données dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md). Vous devez lire cette rubrique avant de continuer.  
  
 Un exemple qui montre le flux de données LOB est disponible dans les exemples du Kit de développement logiciel inclus dans le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Pour plus d’informations, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).  
  
## <a name="streaming-outbound-messages-to-the-adapter"></a>Diffusion en continu des Messages sortants à l’adaptateur  
 L’adaptateur prend en charge les données LOB de bout en bout pour le message de demande pour l’opération UpdateLOB de diffusion en continu.  
  
 Pour prendre en charge la diffusion en continu de bout en bout sur les opérations de UpdateLOB dans le modèle de canal WCF, vous devez :  
  
1.  Définir le **UseAmbientTransaction** liaison de propriété à true.  
  
2.  Implémentez un **System.ServiceModel.Channels.BodyWriter** qui est capable de diffusion en continu les données LOB (exécution en continu sur les données LOB de valeur de nœud).  
  
3.  Effectuer l’opération UpdateLOB au sein d’une étendue de transaction.  
  
4.  Créer le **System.ServiceModel.Message** utilisée pour appeler l’opération en fournissant le corps du message avec ce **BodyWriter** à l’aide de la surcharge appropriée de la **Message.Create** (méthode).  
  
### <a name="setting-the-useambienttransaction-binding-property"></a>Définition de la propriété de liaison de UseAmbientTransaction  
 L’exemple suivant montre comment créer une liaison pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] et définir le **UseAmbientTransaction** propriété de liaison.  
  
```  
// Create binding  
OracleDBBinding odbBinding = new OracleDBBinding();  
  
//set the binding property  
binding.UseAmbientTransaction = true;  
  
```  
  
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
  
### <a name="perform-the-operations-within-a-transaction-scope"></a>Effectuer les opérations au sein d’une étendue de Transaction  
 L’exemple suivant montre comment effectuer des opérations dans une étendue de transaction.  
  
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
  
### <a name="creating-a-message-by-using-a-bodywriter"></a>Création d’un Message à l’aide d’un BodyWriter  
 L’exemple suivant montre comment créer un message de demande de UpdateLOB à l’aide du **BodyWriter** dans l’exemple précédent. Les données du message sont lu à partir d’un fichier.  
  
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
  
## <a name="streaming-inbound-messages-from-the-adapter"></a>Diffusion en continu les Messages entrants à partir de l’adaptateur  
 L’adaptateur prend en charge les données LOB de bout en bout de diffusion en continu pour les messages entrants suivants :  
  
-   Message de réponse pour les fonctions out ou IN OUT qui contiennent des données LOB. Notez que les paramètres de TYPE d’enregistrement peuvent contenir des colonnes de données LOB.  
  
-   Message de réponse pour les fonctions avec des paramètres OUT REF CURSOR (ou valeurs de retour) qui contiennent des données LOB. Cela inclut le côté de la sortie de paramètres dans des REF CURSOR.  
  
-   Message de réponse pour les procédures avec IN ou dans les paramètres qui contiennent des données LOB. Notez que les paramètres de TYPE d’enregistrement peuvent contenir des colonnes de données LOB.  
  
-   Message de réponse pour les procédures avec les paramètres de sortie REF CURSOR qui contiennent des données LOB. Cela inclut le côté de la sortie de paramètres dans des REF CURSOR  
  
-   Message de réponse pour les opérations de SQLEXECUTE qui retournent des jeux de résultats qui contiennent des données LOB.  
  
-   Message de réponse pour la Table ou la vue des opérations Select qui retournent des données LOB dans le résultat est définie.  
  
-   Message de demande pour l’opération POLLINGSTMT (entrante)  
  
 Pour prendre en charge la diffusion en continu de bout en bout sur un message entrant dans le modèle de canal WCF, vous devez :  
  
1.  Implémentez un **System.Xml.XmlDictionaryWriter** qui est capable de diffusion en continu les données LOB (exécution en continu sur les données LOB de valeur de nœud).  
  
2.  Consommer le **Message** en appelant **WriteBodyContents** méthode avec cette **XmlDictionaryWriter**.  
  
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
 L’exemple suivant montre comment utiliser un message de réponse Select de table à l’aide du **FileXmlWriter** implémentée dans l’exemple précédent. (Le **FileWriter** classe a été créé en définissant une sous-classe **XmlDictionaryWriter**.) L’exemple utilise un **IRequestChannel** canal pour appeler l’opération Select. Les détails de la création du canal ont été omis. Le message de requête de sélection est lu à partir d’un fichier et le message de réponse Select est écrite dans un fichier.  
  
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
  
 Le code XML suivant montre le message de demande (contenu du fichier select.xml) pour l’opération de sélection. La table CUSTOMER contient une colonne BLOB nommée PHOTO.  
  
```  
<Select xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER">  
  <COLUMN_NAMES>*</COLUMN_NAMES>  
  <FILTER>NAME='Kim Ralls'</FILTER>  
</Select>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications de base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)