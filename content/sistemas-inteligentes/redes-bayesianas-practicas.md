## Ejercicio sesión 1

| Tipo de relación / (In)dependencia | Independencia                                                                                                                                                                                     | Dependencia                                                                                                                                      |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Marginal                           | No hay **ningún camino** o, **si los hay**, en todos ellos habrá un paso con configuración de **efecto común**.                                                                                   | Hay al menos un camino entre ellas con una configuración de **causa común** o **cadena causal**.                                                 |
| Condicional                        | Los **caminos en los que se pasa por una variable observada** tienen que tener al menos una configuración de **causa común** o **cadena causal** con el **nodo central** siendo el **observado**. | Hay al menos un camino entre ellas con una configuración de **efecto común**, siendo el **nodo central** o un **descendiente** el **observado**. |
- Marginal (A y B)
	- Independencia
		- **No hay ningún camino**.
		- Si los hay, en todos habrá paso con **efecto común**.
			A -> otro <- B
	- Dependencia
		- Hay al menos un camino entre ellas con **causa común** o **cadena causal**.
			- A -> otro -> B
			- A <- otro <- B
			- A <- otro -> B
- Condicional (A y B dado C)
	- Independencia
		- A -> C -> B
		- A <- C <- B
		- A <- C -> B
	- Dependencia
		- Cuando A, B y C tienen alguna configuración de **efecto común**.

> [!example] Ejercicio 7
> Teniendo en cuenta estas indicaciones, crea un grafo que verifique las siguientes relaciones para un problema con 5 variables.
> Ten en cuenta que algunas relaciones pueden modelarse de varias formas.
> - Las variables A y B son marginalmente independientes.
> - Las variables A y C son condicionalmente independientes dada D.
> - Las variables D y E son condicionalmente independientes dada A.
> - Las variables A y B son condicionalmente dependientes dada E.

![[Pasted image 20251209134524.png]]
## Ejercicio sesión 2

Contenido del `main`

```java
InferenceTester obj = new InferenceTester("asia.pgmx");

System.out.format("Network \"%s\" with %d nodes and %d links\n", obj.getProbNet().getName(), obj.getProbNet().getNumNodes(), obj.getProbNet().getLinks().size());

// asking for P(Has bronchitis=no|Dyspnoea?=yes, Smoker?=No)
EvidenceCase evidence = new EvidenceCase();

evidence.addFinding(obj.probNet, "Dyspnoea?", "yes");
evidence.addFinding(obj.probNet, "Smoker?", "no");

List<Variable> variablesOfInterest = Collections.singletonList(obj.probNet.getVariable("Has bronchitis"));

// random query
obj.VEInference(variablesOfInterest, evidence);
obj.setSeed(9762L);

evidence = obj.getRandomEvidence(2);
variablesOfInterest = obj.getRandomVariablesOfInterest(1, evidence);

obj.VEInference(variablesOfInterest, evidence);
```