# Sperner's lemma for the layman

Created: Jul 21, 2020 12:24 AM
Tags: Beauty, Mathematics

I learnt this formulation from episode 27 of My Favorite Theorem and thought it illustrates how mathematics can be beautiful.

Triangulate a spherical ball, i.e. divide the entire surface of the ball into triangles, such that the only way two triangles meet are by either

1. Sharing a corner
2. Sharing a side

It is important to note that there are only finitely many triangles.

Now, randomly mark every corner of every triangle as either $A, B$ or $C$. Since this labeling is *completely random,* we can have triangles labelled as, for example, $AAA$, $CBB$ or $ABC$. In fact, all the nine labelings ([A/B/C][A/B/C][A/B/C]) are possible. 

Sperner's lemma states that if you can find a triangle whose corners are $ABC$; then it is *guaranteed* that there is *at least* one more triangle whose corners are $ABC$. The proof is as follows:

1. Starting out in triangle $ABC$, treat every line segment labelled $AB$ as a door through which you can travel into another triangle.
2. Once you travel into a new triangle, observe that this new triangle also has a side $AB$ (the one through which you just entered this new triangle), thus has two corners labelled $A$ and $B$.
3. The third corner can either be $C$ or one of $A$ and $B$.
    1. If it is $C$, we are done since this new triangle has the labeling $ABC$.
    2. If it is either $A$ or $B$, we just found an new door to travel into.
4. Since there are only finite number of triangles, you will eventually halt somewhere.
5.  But observe that you only halt when you find a triangle labelled $ABC$.
6. Therefore, you will eventually find a triangle labelled $ABC$.

A question you may have is how do we know that the triangle $ABC$ where we halt is not the original triangle itself. The proof of impossibility of this is as follows (reductio ad absurdum)

1. Since you entered this triangle, it must have a side labelled $AB$. Travel backwards into the previous triangle.
2. Since you entered this previous triangle as well, it must also have a side labelled $AB$, which is distinct from the $AB$ you just travelled backwards into. So travel backwards once again.
3. Keep travelling backwards as described in 1 and 2
4. Observe that this is nonsensical since there are only finite number of triangles and you cannot keep travelling backwards indefinitely. This absurdity arises due the false hypothesis that the final triangle $ABC$ is same as the initial triangle $ABC$.
5. Thus, the final triangle and initial triangle are distinct.