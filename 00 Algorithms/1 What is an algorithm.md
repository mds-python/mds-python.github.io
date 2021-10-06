# What is an algorithm?

> **Ingredients:**
> * 1 cup white sugar
> * ½ cup butter
> * 2 eggs
> * 2 teaspoons vanilla extract
> * 1 ½ cups all-purpose flour
> * 1 ¾ teaspoons baking powder
> * ½ cup milk
>
> **Directions:**
> 1. Preheat oven to 175 degrees C.
> 2. Grease and flour a 9x9 inch pan.
> 3. In a medium bowl, cream together the sugar and butter.
> 4. Beat in the eggs, one at a time, then stir in the vanilla.
> 5. Combine flour and baking powder, add to the creamed mixture and mix well.
> 6. Stir in the milk until batter is smooth.
> 7. Pour or spoon batter into the prepared pan.
> 8. Bake for 30 to 40 minutes in the preheated oven. Cake is done when it springs back to the touch.

What you see above is a recipe for a white cake. It contains necessary ingredients and a set of operations you need to perform (directions). The result is a tasty cake. Your first homework will be to make it and offer it to your teacher.

In mathematics or computer world such recipe is called an *algorithm*. It is a finite sequence of well-defined, computer-implementable instructions, typically to solve a class of specific problems or to perform a computation. Usually, it operates on some data (ingredients) and provides some result (the cake).

Algorithms are specified in some **formal language**. It differs from your everyday (*natural*) language in a way, it has very strict rules. To be more precise, see an excerpt from a free on-line book ‘[How to Think Like a Computer Scientist](http://openbookproject.net/thinkcs/python/english3e/)’ by Peter Wentworth, Jeffrey Elkner, Allen B. Downey, and Chris Meyers:

**Natural languages** are the languages that people speak, such as English, Spanish, and French. They were not designed by people (although people try to impose some order on them); they evolved naturally.

**Formal languages** are languages that are designed by people for specific applications. For example, the notation that mathematicians use is a formal language that is particularly good at denoting relationships among numbers and symbols. Chemists use a formal language to represent the chemical structure of molecules. And most importantly:

*Programming languages are formal languages that have been designed to express computations.*

Formal languages tend to have strict rules about syntax. For example, `3+3=6` is a syntactically correct mathematical statement, but `3=+6$` is not. H<sub>2</sub>O is a syntactically correct chemical name, but <sub>2</sub>Zz is not.

Syntax rules come in two flavors, pertaining to **tokens** and structure. Tokens are the basic elements of the language, such as words, numbers, and chemical elements. One of the problems with `3=+6$` is that `$` is not a legal token in mathematics (at least as far as we know). Similarly, <sub>2</sub>Zz is not legal because there is no element with the abbreviation *Zz*.

The second type of syntax rule pertains to the **structure** of a statement — that is, the way the tokens are arranged. The statement `3=+6$` is structurally illegal because you can’t place a plus sign immediately after an equal sign. Similarly, molecular formulas have to have subscripts after the element name, not before.

When you read a sentence in English or a statement in a formal language, you have to figure out what the structure of the sentence is (although in a natural language you do this subconsciously). This process is called **parsing**.

For example, when you hear the sentence, ‘The other shoe fell’, you understand that the other shoe is the subject and fell is the verb. Once you have parsed a sentence, you can figure out what it means, or the **semantics** of the sentence. Assuming that you know what a shoe is and what it means to fall, you will understand the general implication of this sentence.

Although formal and natural languages have many features in common — tokens, structure, syntax, and semantics — there are many differences:

* **ambiguity**
  
  Natural languages are full of ambiguity, which people deal with by using contextual clues and other information. Formal languages are designed to be nearly or completely unambiguous, which means that any statement has exactly one meaning, regardless of context.

* **redundancy**
  
  In order to make up for ambiguity and reduce misunderstandings, natural languages employ lots of redundancy. As a result, they are often verbose. Formal languages are less redundant and more concise.

* **literalness**
  
  Natural languages are full of idiom and metaphor. If someone says, The other shoe fell, there is probably no shoe and nothing falling. Formal languages mean exactly what they say.

People who grow up speaking a natural language—everyone—often have a hard time adjusting to formal languages. In some ways, the difference between formal and natural language is like the difference between poetry and prose, but more so:

* **Poetry**

   Words are used for their sounds as well as for their meaning, and the whole poem together creates an effect or emotional response. Ambiguity is not only common but often deliberate.

* **Prose**

   The literal meaning of words is more important, and the structure contributes more meaning. Prose is more amenable to analysis than poetry but still often ambiguous.

* **Programs**

   The meaning of a computer program is unambiguous and literal, and can be understood entirely by analysis of the tokens and structure.

Here are some suggestions for reading programs (and other formal languages). First, remember that formal languages are much more dense than natural languages, so it takes longer to read them. Also, the structure is very important, so it is usually not a good idea to read from top to bottom, left to right. Instead, learn to parse the program in your head, identifying the tokens and interpreting the structure. Finally, the details matter. Little things like spelling errors and bad punctuation, which you can get away with in natural languages, can make a big difference in a formal language.

<hr/>

Published under [GNU Free Documentation License](https://www.gnu.org/licenses/fdl-1.3.html) license.
