---
title: Tester le service web de BizTalk | Documents Microsoft
description: "Configurer les emplacements de réception et web.config pour tester le service web BizTalk dans un navigateur web"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dc2171d-4abe-43db-b4bc-e484048c6430
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48a35373735102bd75d1c388da29b06d4392ba18
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="test-a-biztalk-web-service"></a><span data-ttu-id="b879d-103">Tester un Service Web BizTalk</span><span class="sxs-lookup"><span data-stu-id="b879d-103">Test a BizTalk Web Service</span></span>

## <a name="overview"></a><span data-ttu-id="b879d-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="b879d-104">Overview</span></span>
<span data-ttu-id="b879d-105">Vous pouvez tester votre service Web publié sans écrire d'application cliente Web.</span><span class="sxs-lookup"><span data-stu-id="b879d-105">You can test your published Web service without writing a Web client application.</span></span> <span data-ttu-id="b879d-106">Vous pouvez utiliser un navigateur Web, tel qu'Internet Explorer, pour tester votre service Web publié.</span><span class="sxs-lookup"><span data-stu-id="b879d-106">You can use a Web browser, such as Internet Explorer, to test your published Web service.</span></span> <span data-ttu-id="b879d-107">Bien que vous puissiez accéder à tout service Web publié à l'aide d'un navigateur Web, vous pouvez uniquement tester les services Web avec des méthodes Web contenant des paramètres de type simple.</span><span class="sxs-lookup"><span data-stu-id="b879d-107">Although you can access any published Web service using a Web browser, you can only test Web services with Web methods that contain simple type parameters.</span></span> <span data-ttu-id="b879d-108">Pour tester votre méthode Web dans un navigateur Web, vos parties de message pour les messages de demande et de réponse qui sont utilisés dans le port de réception peuvent uniquement être un type simple, tel que **System.String** ou **System.Int32**.</span><span class="sxs-lookup"><span data-stu-id="b879d-108">To test your Web method in a Web browser, your message parts for the request and response messages that are used in the receive port can only be a simple type, such as **System.String** or **System.Int32**.</span></span> <span data-ttu-id="b879d-109">Si une partie de message utilise un schéma comme type de message, vous ne pouvez pas tester la méthode Web à l'aide d'un navigateur.</span><span class="sxs-lookup"><span data-stu-id="b879d-109">If any message part uses a schema as a message type, you cannot test the Web method with a browser.</span></span>  
  
 <span data-ttu-id="b879d-110">Si vous voulez tester vos services Web publiés à l'aide de HTTP-GET ou HTTP-POST, vous devez configurer votre emplacement de réception BizTalk pour l'adaptateur SOAP et modifier le fichier Web.config pour votre service Web publié.</span><span class="sxs-lookup"><span data-stu-id="b879d-110">If you want to test your published Web services using HTTP-GET or HTTP-POST, you must configure your BizTalk receive location for the SOAP adapter and modify the Web.config file for your published Web service.</span></span>  
  
 <span data-ttu-id="b879d-111">**Modifier les emplacements de réception**</span><span class="sxs-lookup"><span data-stu-id="b879d-111">**Modifying the Receive Locations**</span></span>  
  
 <span data-ttu-id="b879d-112">Lorsque l'adaptateur SOAP configure des emplacements de réception, il définit normalement l'URI de l'emplacement de réception en donnant les noms du répertoire virtuel et du fichier .asmx du service Web :</span><span class="sxs-lookup"><span data-stu-id="b879d-112">When the SOAP adapter configures receive locations, the SOAP adapter normally sets the URI of the receive location by giving the virtual directory and the Web service .asmx file name:</span></span>  
  
```  
/PurchaseOrder/POOrchestration.asmx  
```  
  
 <span data-ttu-id="b879d-113">Cela permet à l'adaptateur SOAP de recevoir des demandes de service Web à l'aide du protocole HTTP-SOAP.</span><span class="sxs-lookup"><span data-stu-id="b879d-113">This allows the SOAP adapter to receive Web service requests using the HTTP-SOAP protocol.</span></span> <span data-ttu-id="b879d-114">Pour configurer l'emplacement de réception pour utiliser le protocole HTTP-GET ou HTTP-POST, vous devez ajouter le nom de la méthode à l'URI :</span><span class="sxs-lookup"><span data-stu-id="b879d-114">To configure the receive location to use the HTTP-GET or HTTP-POST protocol, you must append the method name to the URI:</span></span>  
  
```  
/PurchaseOrder/POOrchestration.asmx/Operation_1  
```  
  
 <span data-ttu-id="b879d-115">Le nom de la méthode est identique à celui de l'opération de port dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="b879d-115">The method name is the same as the port operation name in the orchestration.</span></span>  
  
 <span data-ttu-id="b879d-116">**Modification du fichier Web.config**</span><span class="sxs-lookup"><span data-stu-id="b879d-116">**Modifying the Web.config file**</span></span>  
  
 <span data-ttu-id="b879d-117">Par défaut, l'Assistant configure les services Web pour utiliser le protocole HTTP-SOAP.</span><span class="sxs-lookup"><span data-stu-id="b879d-117">By default, the wizard configures the Web services to use the HTTP-SOAP protocol.</span></span> <span data-ttu-id="b879d-118">HTTP-GET et HTTP-POST sont explicitement désactivés.</span><span class="sxs-lookup"><span data-stu-id="b879d-118">HTTP-GET and HTTP-POST are explicitly disabled.</span></span> <span data-ttu-id="b879d-119">Pour tester un service Web à l'aide d'un navigateur Web, vous devez activer HTTP-GET.</span><span class="sxs-lookup"><span data-stu-id="b879d-119">To test a Web service with a Web browser, you must enable HTTP-GET.</span></span>  
  
## <a name="update-the-webconfig"></a><span data-ttu-id="b879d-120">Mettre à jour le fichier Web.config</span><span class="sxs-lookup"><span data-stu-id="b879d-120">Update the Web.config</span></span>
  
1.  <span data-ttu-id="b879d-121">Ouvrez le fichier Web.config pour le service Web publié.</span><span class="sxs-lookup"><span data-stu-id="b879d-121">Open the Web.config file for the published Web service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b879d-122">Vous pouvez trouver le fichier Web.config dans le répertoire que vous avez configuré pour la racine virtuelle IIS contenant le service Web.</span><span class="sxs-lookup"><span data-stu-id="b879d-122">You can find the Web.config file in the directory that you configured for the IIS virtual root that contains the Web service.</span></span>  
  
2.  <span data-ttu-id="b879d-123">Rechercher les \<protocoles\> section :</span><span class="sxs-lookup"><span data-stu-id="b879d-123">Find the \<protocols\> section:</span></span>  
  
    ```  
    <webServices>  
       <protocols>  
         <remove name="HttpPost" />  
         <remove name="HttpGet" />  
         <remove name="HttpPostLocalhost" />  
       </protocols>  
  
    </webServices>  
    ```  
  
3.  <span data-ttu-id="b879d-124">Pour tester HTTP-GET, HTTP-POST ou HTTP-POST depuis l’ordinateur local, supprimez la ligne correspondante à partir de la \<protocoles\> section.</span><span class="sxs-lookup"><span data-stu-id="b879d-124">For testing HTTP-GET, HTTP-POST, or HTTP-POST from the local computer, remove the corresponding line from the \<protocols\> section.</span></span>  
  
 <span data-ttu-id="b879d-125">Pour plus d’informations sur les options de configuration, consultez [Options de Configuration pour les Services Web XML créés à l’aide d’ASP.NET](https://msdn.microsoft.com/library/b2c0ew36.aspx).</span><span class="sxs-lookup"><span data-stu-id="b879d-125">For more information about the configuration options, see [Configuration Options for XML Web Services Created Using ASP.NET](https://msdn.microsoft.com/library/b2c0ew36.aspx).</span></span> 
  
#### <a name="access-a-web-service-with-internet-explorer"></a><span data-ttu-id="b879d-126">Accéder à un service Web avec Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="b879d-126">Access a Web service with Internet Explorer</span></span>  
  
-   <span data-ttu-id="b879d-127">Dans Internet Explorer, dans le **adresse** zone, tapez l’URL du service Web en utilisant le format **http://*nom_serveur*/*apppath* / *webservicename*.asmx**.</span><span class="sxs-lookup"><span data-stu-id="b879d-127">In Internet Explorer, in the **Address** box, type the URL for the Web service using the format **http://*servername*/*apppath*/*webservicename*.asmx**.</span></span>  
  
    |<span data-ttu-id="b879d-128">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b879d-128">Parameter</span></span>|<span data-ttu-id="b879d-129">Valeur</span><span class="sxs-lookup"><span data-stu-id="b879d-129">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="b879d-130">***servername***</span><span class="sxs-lookup"><span data-stu-id="b879d-130">***servername***</span></span>|<span data-ttu-id="b879d-131">Nom du serveur sur lequel vous avez déployé le service Web XML.</span><span class="sxs-lookup"><span data-stu-id="b879d-131">The name of the server that you have deployed your XML Web service.</span></span>|  
    |<span data-ttu-id="b879d-132">***Apppath***</span><span class="sxs-lookup"><span data-stu-id="b879d-132">***Apppath***</span></span>|<span data-ttu-id="b879d-133">Nom du répertoire virtuel et chemin d'accès à l'application Web</span><span class="sxs-lookup"><span data-stu-id="b879d-133">The name of your virtual directory and the Web application path.</span></span>|  
    |<span data-ttu-id="b879d-134">***webservicename.asmx***</span><span class="sxs-lookup"><span data-stu-id="b879d-134">***webservicename.asmx***</span></span>|<span data-ttu-id="b879d-135">Nom du fichier .asmx de service Web XML</span><span class="sxs-lookup"><span data-stu-id="b879d-135">The name of the XML Web service .asmx file.</span></span>|  
  
 <span data-ttu-id="b879d-136">La description du service Web vous montre toutes les méthodes de service Web prises en charge par le service Web particulier.</span><span class="sxs-lookup"><span data-stu-id="b879d-136">The description for the Web service shows you all the Web service methods that the particular Web service supports.</span></span> <span data-ttu-id="b879d-137">La page de description du service Web contient des liens pour chaque méthode Web disponible et la description du service Web.</span><span class="sxs-lookup"><span data-stu-id="b879d-137">The Web service description page contains links for each available Web method and the service description of the Web service.</span></span>  
  
#### <a name="test-a-web-service-with-internet-explorer-using-http-get"></a><span data-ttu-id="b879d-138">Tester un service Web avec Internet Explorer à l’aide de HTTP-GET</span><span class="sxs-lookup"><span data-stu-id="b879d-138">Test a Web service with Internet Explorer using HTTP-GET</span></span>  
  
1.  <span data-ttu-id="b879d-139">Après avoir accédé à la page de description du service Web, cliquez sur l'une des méthodes Web répertoriées dans cette page.</span><span class="sxs-lookup"><span data-stu-id="b879d-139">After accessing the Web service description page, click one of the Web methods listed in the Web service description page.</span></span>  
  
2.  <span data-ttu-id="b879d-140">Les paramètres nécessaires pour la méthode Web, puis tapez **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="b879d-140">Type the necessary parameters for the Web method, and then click **Invoke**.</span></span>  
  
3.  <span data-ttu-id="b879d-141">Le serveur renvoie une réponse XML dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="b879d-141">The server returns an XML response in the browser.</span></span> <span data-ttu-id="b879d-142">Si le type de données renvoyées pour le service Web est un nombre à virgule flottante double précision, le résultat doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="b879d-142">If the return data type for the Web service is a double-precision floating-point number, the result might look like the following:</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <double>74.5</double>  
    ```  
  
#### <a name="test-a-web-service-with-internet-explorer-using-http-get-alternate-method"></a><span data-ttu-id="b879d-143">Tester un service Web avec Internet Explorer à l’aide de HTTP-GET (autre méthode)</span><span class="sxs-lookup"><span data-stu-id="b879d-143">Test a Web service with Internet Explorer using HTTP-GET (alternate method)</span></span>  
  
1.  <span data-ttu-id="b879d-144">Dans Internet Explorer, dans le **adresse** zone, tapez l’URL du service Web en utilisant le format ***http://servername/vdir/webservicename.asmx/Methodname?parameter=value***.</span><span class="sxs-lookup"><span data-stu-id="b879d-144">In Internet Explorer, in the **Address** box, type the URL for the Web service using the format ***http://servername/vdir/webservicename.asmx/Methodname?parameter=value***.</span></span>  
  
    |<span data-ttu-id="b879d-145">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b879d-145">Parameter</span></span>|<span data-ttu-id="b879d-146">Valeur</span><span class="sxs-lookup"><span data-stu-id="b879d-146">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="b879d-147">***servername***</span><span class="sxs-lookup"><span data-stu-id="b879d-147">***servername***</span></span>|<span data-ttu-id="b879d-148">Nom du serveur sur lequel vous avez déployé le service Web XML.</span><span class="sxs-lookup"><span data-stu-id="b879d-148">The name of the server that you have deployed your XML Web service.</span></span>|  
    |<span data-ttu-id="b879d-149">***Apppath***</span><span class="sxs-lookup"><span data-stu-id="b879d-149">***Apppath***</span></span>|<span data-ttu-id="b879d-150">Nom du répertoire virtuel et chemin d'accès à l'application Web</span><span class="sxs-lookup"><span data-stu-id="b879d-150">The name of your virtual directory and the Web application path.</span></span>|  
    |<span data-ttu-id="b879d-151">***webservicename.asmx***</span><span class="sxs-lookup"><span data-stu-id="b879d-151">***webservicename.asmx***</span></span>|<span data-ttu-id="b879d-152">Nom du fichier .asmx de service Web XML</span><span class="sxs-lookup"><span data-stu-id="b879d-152">The name of the XML Web service .asmx file.</span></span>|  
    |<span data-ttu-id="b879d-153">***MethodName***</span><span class="sxs-lookup"><span data-stu-id="b879d-153">***Methodname***</span></span>|<span data-ttu-id="b879d-154">Nom d'une méthode publique que le service Web XML expose.</span><span class="sxs-lookup"><span data-stu-id="b879d-154">The name of a public method that the XML Web service exposes.</span></span> <span data-ttu-id="b879d-155">Si vous n'indiquez rien, la page de description du service Web XML apparaît, répertoriant chaque méthode publique disponible dans le fichier .asmx.</span><span class="sxs-lookup"><span data-stu-id="b879d-155">If left blank, the description page for the XML Web service appears, listing each public method available in the .asmx file.</span></span> <span data-ttu-id="b879d-156">(Facultatif)</span><span class="sxs-lookup"><span data-stu-id="b879d-156">(Optional)</span></span>|  
    |<span data-ttu-id="b879d-157">***parameter***</span><span class="sxs-lookup"><span data-stu-id="b879d-157">***parameter***</span></span>|<span data-ttu-id="b879d-158">Nom du paramètre approprié et valeur des paramètres requis par votre méthode.</span><span class="sxs-lookup"><span data-stu-id="b879d-158">The appropriate parameter name and value for any parameters required by your method.</span></span> <span data-ttu-id="b879d-159">Si vous n'indiquez rien, la page de description du service Web XML apparaît, répertoriant chaque méthode publique disponible dans le fichier .asmx.</span><span class="sxs-lookup"><span data-stu-id="b879d-159">If left blank, the description page for the XML Web service appears, listing each public method available in the .asmx file.</span></span> <span data-ttu-id="b879d-160">(Facultatif)</span><span class="sxs-lookup"><span data-stu-id="b879d-160">(Optional)</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="b879d-161">Dans cette syntaxe, le nom de la méthode de service Web XML est sensible à la casse, contrairement aux noms du serveur, du projet et du service Web XML.</span><span class="sxs-lookup"><span data-stu-id="b879d-161">The XML Web service method name in this syntax is case sensitive, but the server, project, and XML Web service names are not.</span></span>  
  
2.  <span data-ttu-id="b879d-162">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="b879d-162">Press Enter.</span></span> <span data-ttu-id="b879d-163">Le navigateur Web affiche une réponse XML à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="b879d-163">The Web browser displays an XML response from the server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b879d-164">Vous pouvez également utiliser HTTP-POST pour appeler le service Web.</span><span class="sxs-lookup"><span data-stu-id="b879d-164">You can also use HTTP-POST to call the Web service.</span></span> <span data-ttu-id="b879d-165">Pour plus d’informations et des exemples d’appel de services Web XML à partir d’un navigateur Web, consultez [Access XML Web Services à partir d’un navigateur](https://msdn.microsoft.com/library/45fez2a8.aspx).</span><span class="sxs-lookup"><span data-stu-id="b879d-165">For information and samples about calling XML Web services from a Web browser, see [Access XML Web Services from a Browser](https://msdn.microsoft.com/library/45fez2a8.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b879d-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b879d-166">See Also</span></span>  
 [<span data-ttu-id="b879d-167">Test des services web publiés</span><span class="sxs-lookup"><span data-stu-id="b879d-167">Testing Published Web Services</span></span>](../core/testing-published-web-services.md)