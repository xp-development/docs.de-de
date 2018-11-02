---
title: Durable Azure Functions – serverlose apps
description: Permanente Azure-Funktionen erweitern die Azure Functions-Laufzeit, um zustandsbehaftete Workflows in Code zu aktivieren.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 03197ad57813b8132fe592f4e555c6a35edbd9bd
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "49369955"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="e65f7-103">Permanenten Azure-Funktionen</span><span class="sxs-lookup"><span data-stu-id="e65f7-103">Durable Azure functions</span></span>

<span data-ttu-id="e65f7-104">Wenn Sie mit Azure Functions serverlose Anwendungen zu erstellen, werden Ihre Vorgänge in der Regel entworfen werden, in eine statusfreie Weise ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="e65f7-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="e65f7-105">Der Grund für diese entwurfsentscheidung liegt als die Skalierung der Plattform, wird es schwierig, Sie wissen, welche Server der Code ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e65f7-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="e65f7-106">Es wird auch nur schwer erkennbar, wie viele Instanzen zu einem bestimmten Zeitpunkt aktiv sind.</span><span class="sxs-lookup"><span data-stu-id="e65f7-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="e65f7-107">Es gibt jedoch Klassen von Anwendungen, die den aktuellen Status eines Prozesses nicht bekannt sein müssen.</span><span class="sxs-lookup"><span data-stu-id="e65f7-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="e65f7-108">Betrachten Sie den Prozess zur Übermittlung einer Bestellung zu einem Onlineshop.</span><span class="sxs-lookup"><span data-stu-id="e65f7-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="e65f7-109">Der Auscheckvorgang möglicherweise einen Workflow, der mehrere Vorgänge besteht, die den Zustand des Prozesses kennen müssen.</span><span class="sxs-lookup"><span data-stu-id="e65f7-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="e65f7-110">Solche Informationen gehören möglicherweise die Produktbestands, wenn der Kunde Form von Credits auf ihr Konto und die Ergebnisse der Verarbeitung der Kreditkarte verfügt.</span><span class="sxs-lookup"><span data-stu-id="e65f7-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="e65f7-111">Diese Vorgänge ist möglicherweise einfach eigene interne Workflows oder sogar Dienste von Drittanbietern.</span><span class="sxs-lookup"><span data-stu-id="e65f7-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="e65f7-112">Heute sind verschiedene Muster, Unterstützung mit der Koordinierung von Anwendungsstatus zwischen internen und externen Systemen.</span><span class="sxs-lookup"><span data-stu-id="e65f7-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="e65f7-113">Es ist üblich, stoßen auf Lösungen, die zentralisierte warteschlangensysteme, verteilter Schlüssel-Wert-Speicher oder freigegebene Datenbanken zur Verwaltung dieses Zustands verwenden.</span><span class="sxs-lookup"><span data-stu-id="e65f7-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="e65f7-114">Diese sind jedoch alle zusätzlichen Ressourcen, die jetzt bereitgestellt und verwaltet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="e65f7-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="e65f7-115">In einer serverlosen Umgebung kann Ihr Code koordinierte mit diesen Ressourcen manuell sehr aufwändig.</span><span class="sxs-lookup"><span data-stu-id="e65f7-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="e65f7-116">Azure Functions bietet eine Alternative zum Erstellen von zustandsbehafteter Funktionen, die Durable Functions aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="e65f7-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="e65f7-117">Durable Functions ist eine Erweiterung für Azure Functions-Laufzeit, die die Definition der zustandsbehaftete Workflows in Code ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="e65f7-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="e65f7-118">Die Erweiterung Durable Functions können Sie Workflows in Aktivitäten aufteilen, Verwalten des Zustands, Fortschritt Prüfpunkte erstellen und behandeln die Verteilung von Funktionsaufrufen auf Servern.</span><span class="sxs-lookup"><span data-stu-id="e65f7-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="e65f7-119">Im Hintergrund ist es, mithilfe von Azure Storage-Konto der Ausführungsverlauf beibehalten, Planen aktivitätsfunktionen und Abrufen von Antworten.</span><span class="sxs-lookup"><span data-stu-id="e65f7-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="e65f7-120">Ihrem serverlose Code nie dauerhaft gespeicherten Informationen in diesem Speicherkonto interagieren soll, und ist in der Regel nicht etwas mit dem Entwickler interagieren müssen.</span><span class="sxs-lookup"><span data-stu-id="e65f7-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="e65f7-121">Auslösen eines zustandsbehafteten Workflows</span><span class="sxs-lookup"><span data-stu-id="e65f7-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="e65f7-122">Zustandsbehaftete Workflows in Durable Functions können in zwei systeminterne Komponenten aufgeteilt werden; Orchestrierung und Aktivität von Triggern.</span><span class="sxs-lookup"><span data-stu-id="e65f7-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="e65f7-123">Trigger und Bindungen sind Kernkomponenten, die von Azure Functions verwendet werden, um Ihre serverlosen Funktionen benachrichtigt, wenn die Eingabe starten, erhalten und Ergebnisse zurückgeben zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="e65f7-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="e65f7-124">Arbeiten mit den orchestrierungsclient</span><span class="sxs-lookup"><span data-stu-id="e65f7-124">Working with the Orchestration client</span></span>

<span data-ttu-id="e65f7-125">Orchestrierungen sind eindeutig, im Vergleich zu anderen Arten der ausgelösten Vorgänge in Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="e65f7-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="e65f7-126">Durable Functions ermöglicht die Ausführung von Funktionen, die Stunden dauern oder sogar Tage ausführen können.</span><span class="sxs-lookup"><span data-stu-id="e65f7-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="e65f7-127">Diese Art von Verhalten wird in der Lage sein, um den Status einer ausgeführten Orchestrierung überprüfen müssen, bereits im Vorfeld zu beenden, oder senden Sie Benachrichtigungen über externe Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="e65f7-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="e65f7-128">In solchen Fällen enthält die Erweiterung Durable Functions die `DurableOrchestrationClient` -Klasse, die Ihnen ermöglicht, die Interaktion mit orchestriert Funktionen.</span><span class="sxs-lookup"><span data-stu-id="e65f7-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="e65f7-129">Sie erhalten Sie Zugriff auf den orchestrierungsclient mithilfe der `OrchestrationClientAttribute` Bindung.</span><span class="sxs-lookup"><span data-stu-id="e65f7-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="e65f7-130">In der Regel ist, schließen Sie dieses Attribut mit einem anderen Triggertyp, z. B. eine `HttpTrigger` oder `ServiceBusTrigger`.</span><span class="sxs-lookup"><span data-stu-id="e65f7-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="e65f7-131">Nachdem die Quelle-Funktion ausgelöst wurde, kann der orchestrierungsclient zu einer Orchestrator-Funktion verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e65f7-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

```csharp
[FunctionName("KickOff")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient<orchestrationClient>)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

### <a name="the-orchestrator-function"></a><span data-ttu-id="e65f7-132">Der Orchestrator-Funktion</span><span class="sxs-lookup"><span data-stu-id="e65f7-132">The orchestrator function</span></span>

<span data-ttu-id="e65f7-133">Hinzufügen einer Anmerkung zu einer Funktion mit dem OrchestrationTriggerAttribute in Azure Functions ein diese Funktion als eine orchestratorfunktion.</span><span class="sxs-lookup"><span data-stu-id="e65f7-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="e65f7-134">Er ist verantwortlich für die verschiedenen Aktivitäten, aus denen Ihre zustandsbehaftete Workflows verwalten.</span><span class="sxs-lookup"><span data-stu-id="e65f7-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="e65f7-135">Orchestratorfunktionen können keine vorgenommen werden Bindungen die OrchestrationTriggerAttribute verwenden.</span><span class="sxs-lookup"><span data-stu-id="e65f7-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="e65f7-136">Dieses Attribut kann nur mit dem Parametertyp DurableOrchestrationContext verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e65f7-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="e65f7-137">Keine anderen Eingaben können verwendet werden, da die Deserialisierung von Eingaben in die Funktionssignatur wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e65f7-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="e65f7-138">Zum Abrufen von Eingaben von der orchestrierungsclientbindung, die GetInput\<T\> Methode muss verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e65f7-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="e65f7-139">Darüber hinaus die Rückgabetypen der Orchestrierungsfunktionen muss entweder "void", Task oder einen serialisierbaren JSON-Wert.</span><span class="sxs-lookup"><span data-stu-id="e65f7-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="e65f7-140">*Code für die Fehlerbehandlung wurde aus Gründen der Übersichtlichkeit ausgelassen wurde*</span><span class="sxs-lookup"><span data-stu-id="e65f7-140">*Error handling code has been left out for brevity*</span></span>

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<string>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

<span data-ttu-id="e65f7-141">Zur gleichen Zeit können in mehreren Instanzen einer Orchestrierung gestartet und ausgeführt sein.</span><span class="sxs-lookup"><span data-stu-id="e65f7-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="e65f7-142">Aufrufen der `StartNewAsync` Methode für die `DurableOrchestrationClient` startet eine neue Instanz der Orchestrierung.</span><span class="sxs-lookup"><span data-stu-id="e65f7-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="e65f7-143">Die Methode gibt eine `Task<string>` , die abgeschlossen wird, wenn die Orchestrierung gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="e65f7-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="e65f7-144">Eine Ausnahme vom Typ `TimeoutException` ruft ausgelöst, wenn die Orchestrierung nicht innerhalb von 30 Sekunden gestartet.</span><span class="sxs-lookup"><span data-stu-id="e65f7-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="e65f7-145">Die abgeschlossene `Task<string>` aus `StartNewAsync` sollten enthält die eindeutige ID der Orchestrierungsinstanz.</span><span class="sxs-lookup"><span data-stu-id="e65f7-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="e65f7-146">Diese Instanz-ID kann verwendet werden, um Vorgänge für diese bestimmte Orchestrierung aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="e65f7-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="e65f7-147">Die Orchestrierung kann abgefragt werden, für den Status oder ereignisbenachrichtigungen gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="e65f7-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="e65f7-148">Der aktivitätsfunktionen</span><span class="sxs-lookup"><span data-stu-id="e65f7-148">The activity functions</span></span>

<span data-ttu-id="e65f7-149">Aktivitätsfunktionen sind die diskreten Vorgänge, die zusammen in einer Orchestrierungsfunktion zum Erstellen des Workflows erstellt zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="e65f7-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="e65f7-150">Hier ist, in denen meisten der eigentlichen Arbeit durchgeführt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="e65f7-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="e65f7-151">Sie stellen die Geschäftslogik dar, die lang ausgeführte Prozesse, und die Puzzleteile zu einer größeren Lösung.</span><span class="sxs-lookup"><span data-stu-id="e65f7-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="e65f7-152">Die `ActivityTriggerAttribute` wird verwendet, um einen Funktionsparameter vom Typ mit Anmerkungen versehen `DurableActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="e65f7-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="e65f7-153">Mithilfe der-Anmerkung informiert die Laufzeit an, dass die Funktion als eine aktivitätsfunktion verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="e65f7-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="e65f7-154">Eingabewerte für aktivitätsfunktionen werden abgerufen, mit der `GetInput<T>` Methode der `DurableActivityContext` Parameter.</span><span class="sxs-lookup"><span data-stu-id="e65f7-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="e65f7-155">Ähnlich wie Orchestrierungsfunktionen, die Rückgabetypen der aktivitätsfunktionen muss entweder "void", Task oder einen serialisierbaren JSON-Wert.</span><span class="sxs-lookup"><span data-stu-id="e65f7-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="e65f7-156">Alle nicht behandelten Ausnahmen, die in aktivitätsfunktionen werden gesendet, wird an die aufrufende orchestratorfunktion und als eine `TaskFailedException`.</span><span class="sxs-lookup"><span data-stu-id="e65f7-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="e65f7-157">An diesem Punkt wird der Fehler abgefangen und protokolliert Sie in der Orchestrator werden kann, und die Aktivität wiederholt werden kann.</span><span class="sxs-lookup"><span data-stu-id="e65f7-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="e65f7-158">Empfohlene Ressourcen</span><span class="sxs-lookup"><span data-stu-id="e65f7-158">Recommended resources</span></span>

* [<span data-ttu-id="e65f7-159">Durable Functions</span><span class="sxs-lookup"><span data-stu-id="e65f7-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [<span data-ttu-id="e65f7-160">Bindungen für Durable Functions</span><span class="sxs-lookup"><span data-stu-id="e65f7-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [<span data-ttu-id="e65f7-161">Verwalten von Instanzen in Durable Functions</span><span class="sxs-lookup"><span data-stu-id="e65f7-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
<span data-ttu-id="e65f7-162">[Zurück](event-grid.md)
[Weiter](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="e65f7-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>