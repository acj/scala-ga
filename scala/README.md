# A simple genetic algorithm written in Scala

## Usage

See `GAWorksheet.sc`:

```scala
var targetString = "TheQuickBrownFoxJumpedOverTheLazyDog"
var targetFitness = targetString.length

var popSize = 10
var chromosomeSize = targetString.length
var pop = Seq.fill(popSize)(Chromosome.generateChromosome(chromosomeSize)).toList

var fitnessFunction = {
  def countMatchingChars( pairs: List[(Char, Char)] ): Float =
    pairs map((chars: (Char, Char)) => chars match { case (c1, c2) => if (c1 == c2) 1 else 0 }) sum
  		 
  ((c: Chromosome) => countMatchingChars(c.getGenes zip targetString))
}

var ga = new GeneticAlgorithm(pop, fitnessFunction, targetFitness)

ga evolve
```

## License

If this is worth using, modifying, or sharing, then feel free to do so.
