---
title: Exemple de GetMessages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29e575fa-d68b-4975-84b8-da4f17bd2db3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2ebc4ce5b87a0b698f0295fdf29c8f7138efed7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getmessages-sample"></a><span data-ttu-id="1a284-102">Exemple de GetMessages</span><span class="sxs-lookup"><span data-stu-id="1a284-102">GetMessages Sample</span></span>
<span data-ttu-id="1a284-103">Cette rubrique fournit des exemples de code que vous pouvez utiliser pour récupérer des messages à partir d’une des tables de non répudiation de message ou une des tables de métier (LOB) dans un format lisible.</span><span class="sxs-lookup"><span data-stu-id="1a284-103">This topic provides sample code that you can use to retrieve messages from one of the message non-repudiation tables or one of the line-of-business (LOB) tables in a readable form.</span></span> <span data-ttu-id="1a284-104">Les tables de non répudiation de message incluent MessageStorageIn et MessageStorageOut de la [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]base de données Archive ; les tables LOB incluent MessageFromLOB et MessageToLOB dans les [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]base de données.</span><span class="sxs-lookup"><span data-stu-id="1a284-104">The message non-repudiation tables include MessageStorageIn and MessageStorageOut in the [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]Archive database; the LOB tables include MessageFromLOB and MessageToLOB in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA database.</span></span>  
  
 <span data-ttu-id="1a284-105">Utilisez `GetMessages` pour le dépannage ou développement.</span><span class="sxs-lookup"><span data-stu-id="1a284-105">Use `GetMessages` for either troubleshooting or development.</span></span> <span data-ttu-id="1a284-106">Par défaut, le code retourne une chaîne en base 64.</span><span class="sxs-lookup"><span data-stu-id="1a284-106">By default, the code returns a base 64 string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a284-107">L’exemple de code GetMessages.cs contient deux sections de code : un pour la récupération des messages à partir d’une des tables LOB et un pour la récupération des messages à partir d’une des tables de non répudiation.</span><span class="sxs-lookup"><span data-stu-id="1a284-107">The GetMessages.cs sample code contains two sections of code—one for retrieving messages from one of the LOB tables, and one for retrieving messages from one of the non-repudiation tables.</span></span> <span data-ttu-id="1a284-108">Créer des applications distinctes pour chaque objectif.</span><span class="sxs-lookup"><span data-stu-id="1a284-108">Create separate applications for each purpose.</span></span>  
  
### <a name="to-retrieve-messages-from-an-lob-table"></a><span data-ttu-id="1a284-109">Pour récupérer des messages à partir d’une table LOB</span><span class="sxs-lookup"><span data-stu-id="1a284-109">To retrieve messages from an LOB table</span></span>  
  
1.  <span data-ttu-id="1a284-110">Ajoutez le code suivant à votre programme :</span><span class="sxs-lookup"><span data-stu-id="1a284-110">Add the following sample code to your program:</span></span>  
  
     `private static string GetLOBMessage(string sMessageSource, string sMessageID)`  
  
2.  <span data-ttu-id="1a284-111">Définir le `sMessageSource` paramètre à la table MessagesToLOB ou MessagesFromLOB.</span><span class="sxs-lookup"><span data-stu-id="1a284-111">Set the `sMessageSource` parameter to either the MessagesFromLOB or MessagesToLOB table.</span></span>  
  
3.  <span data-ttu-id="1a284-112">Définir le `sMessageID` paramètre à la valeur de la **MessageID** champ dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="1a284-112">Set the `sMessageID` parameter to the value of the **MessageID** field in the database.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1a284-113">L’application retourne une chaîne qui contient le message récupéré.</span><span class="sxs-lookup"><span data-stu-id="1a284-113">The application returns a string that contains the retrieved message.</span></span>  
  
### <a name="to-retrieve-messages-from-a-non-repudiation-table"></a><span data-ttu-id="1a284-114">Pour récupérer des messages à partir d’une table de non répudiation</span><span class="sxs-lookup"><span data-stu-id="1a284-114">To retrieve messages from a non-repudiation table</span></span>  
  
1.  <span data-ttu-id="1a284-115">Ajoutez le code suivant à votre programme :</span><span class="sxs-lookup"><span data-stu-id="1a284-115">Add the following sample code to your program:</span></span>  
  
     `private static string GetNRMessage(string sMessageSource, string sMessageID)`  
  
2.  <span data-ttu-id="1a284-116">Définir le `sMessageSource` paramètre soit la table MessageStorageIn ou MessageStorageOut.</span><span class="sxs-lookup"><span data-stu-id="1a284-116">Set the `sMessageSource` parameter to either the MessageStorageIn or MessageStorageOut table.</span></span>  
  
3.  <span data-ttu-id="1a284-117">Définir le `sMessageID` paramètre à la valeur de la **RecordID** champ dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="1a284-117">Set the `sMessageID` parameter to the value of the **RecordID** field in the database.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1a284-118">L’application retourne une chaîne qui contient le message récupéré.</span><span class="sxs-lookup"><span data-stu-id="1a284-118">The application returns a string that contains the retrieved message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1a284-119">Montre</span><span class="sxs-lookup"><span data-stu-id="1a284-119">Demonstrates</span></span>  
 <span data-ttu-id="1a284-120">L’exemple de GetMessages inclut les deux sections de code suivantes :</span><span class="sxs-lookup"><span data-stu-id="1a284-120">The GetMessages sample includes the following two sections of code:</span></span>  
  
-   <span data-ttu-id="1a284-121">Une section vous montre comment récupérer un message binaire à partir d’une des tables non répudiation et le convertir en format ASCII lisible.</span><span class="sxs-lookup"><span data-stu-id="1a284-121">One section shows you how to retrieve a binary message from one of the non-repudiation tables, and convert it into readable ASCII form.</span></span>  
  
-   <span data-ttu-id="1a284-122">L’autre section vous montre comment récupérer un message à partir d’une des tables LOB.</span><span class="sxs-lookup"><span data-stu-id="1a284-122">The other section shows you how to retrieve a message from one of the LOB tables.</span></span> <span data-ttu-id="1a284-123">Un message dans une table LOB étant déjà sous forme de ASCII, il s’agit d’une instruction SQL select.</span><span class="sxs-lookup"><span data-stu-id="1a284-123">Because a message in an LOB table is already in ASCII form, this is a SQL select statement.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1a284-124">À des fins de démonstration, l’exemple de code fourni utilise une instruction SQL directe qui est sujette aux vulnérabilités d’injection SQL.</span><span class="sxs-lookup"><span data-stu-id="1a284-124">For demonstration purposes, the sample code provided uses a direct SQL statement that is prone to SQL injection vulnerabilities.</span></span> <span data-ttu-id="1a284-125">Dans un environnement de production, il est recommandé d’utiliser des procédures stockées SQL paramétrées, plutôt que l’instruction SQL directe, pour empêcher ces vulnérabilités.</span><span class="sxs-lookup"><span data-stu-id="1a284-125">In a production environment, it is recommended that you use parameterized SQL stored procedures, instead of the direct SQL statement, to prevent such vulnerabilities.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a284-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="1a284-126">Example</span></span>  
 <span data-ttu-id="1a284-127">Utilisez une des deux sections dans l’exemple de code suivant pour la récupération des messages à partir d’une des tables non répudiation ou une des tables LOB.</span><span class="sxs-lookup"><span data-stu-id="1a284-127">Use one of the two sections in the following code example for retrieving messages from one of the non-repudiation tables or one of the LOB tables.</span></span>  
  
```  
using System;  
using System.Text;  
using System.Data.SqlClient;   
using Microsoft.Solutions.BTARN.Shared;  
  
namespace Microsoft.Solutions.BTARN.Admin  
{  
  
      /// <summary>  
      /// Summary description for GetMessages.  
      /// </summary>  
      class GetMessages  
      {  
            /// <summary>  
            /// The main entry point for the application.  
            /// </summary>  
            [STAThread]  
            static void Main(string[] args)  
            {  
                  Console.WriteLine(GetLOBMessage("MessagesFromLOB", "bce5b580daf543a990a4f37331f31e42"));  
                  Console.WriteLine(GetLOBMessage("MessagesToLOB", "bce5b580daf543a990a4f37331f31e42"));  
                  Console.WriteLine(GetNRMessage("MessageStorageIn", "dc06e9cfecd746a889dd6ea7beb3ba21"));  
                  Console.WriteLine(GetNRMessage("MessageStorageOut", "dc06e9cfecd746a889dd6ea7beb3ba21"));  
            }  
  
            /// <summary>  
            /// Retrieve a message from the LOB tables in the BTARNDATA database  
            /// </summary>  
            /// <param name="sMessageSource">Can be either MessagesFromLOB or MessagesToLOB</param>  
            /// <param name="sMessageID">The value of the MessageID field in the database</param>  
            /// <returns>Returns a string that contains the retrieved message</returns>        
            private static string GetLOBMessage(string sMessageSource, string sMessageID)  
            {  
                  SqlDataReader localReader = null;  
                  SqlConnection sqlConnection = null;  
                  SqlCommand sqlCommand = null;  
                  string sReturnedMessage="";              
                  string sQuery;  
  
                  sqlConnection = new SqlConnection(RuntimeGlobal.DataDbConnectionString);  
                  sQuery = "SELECT ServiceContent from " + sMessageSource + " WHERE MessageID=N'" + sMessageID +"'";  
  
                  sqlCommand = new SqlCommand(sQuery, sqlConnection);  
                  sqlConnection.Open();  
  
                  localReader = sqlCommand.ExecuteReader();  
  
                  if (localReader.Read())  
                        sReturnedMessage=localReader.GetString(0);  
  
                  localReader.Close();  
                  sqlConnection.Close();        
                  return sReturnedMessage;              
            }  
  
            /// <summary>  
            /// Retrieve a message from the non-repudiation tables in the BTARNArchive database  
            /// </summary>  
            /// <param name="sMessageSource">Can be either MessageStorageIn or MessageStorageOut</param>  
            /// <param name="sMessageID">The value of the RecordID field in the database</param>  
            /// <returns>Returns a string that contains the retrieved message</returns>  
            private static string GetNRMessage(string sMessageSource, string sMessageID)  
            {  
                  SqlDataReader localReader = null;  
                  SqlConnection sqlConnection = null;  
                  SqlCommand sqlCommand = null;  
                  string sReturnedMessage="";              
                  string sQuery;  
  
                  sqlConnection = new SqlConnection(RuntimeGlobal.ArchiveDbConnectionString);  
                  sQuery = "SELECT Content from " + sMessageSource + " WHERE RecordID=N'" + sMessageID +"'";  
  
                  sqlCommand = new SqlCommand(sQuery, sqlConnection);  
                  sqlConnection.Open();  
  
                  localReader = sqlCommand.ExecuteReader();  
  
                  if (localReader.Read())  
                  {  
                        //Determine the size of the field in bytes and create a new byte array  
                        byte[] bData= new byte[localReader.GetBytes(0, 0, null, 0, 0)];  
  
                        //Read the value of the field into bData  
                        localReader.GetBytes(0, 0, bData, 0, bData.Length);  
  
                        //Convert the byte array into a string  
                        sReturnedMessage=Encoding.ASCII.GetString(bData);  
                  }  
  
                  localReader.Close();  
                  sqlConnection.Close();        
                  return sReturnedMessage;              
            }  
      }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a284-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a284-128">See Also</span></span>  
 [<span data-ttu-id="1a284-129">Exemples de messagerie</span><span class="sxs-lookup"><span data-stu-id="1a284-129">Messaging Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/messaging-samples.md)