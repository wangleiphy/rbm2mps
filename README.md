# Transforming an RBM into an MPS

These are demonstration codes for the Sec.II of [arXiv.17799849 ](https://arxiv.org/submit/1779849). You are free to use them. Please kindly cite the paper 
- Jing Chen, Song Cheng, Haidong Xie, Lei Wang, and Tao Xiang, "On the Equivalence of Restricted Boltzmann Machines and Tensor Network States", [arXiv.17799849 ](https://arxiv.org/submit/1779849)


We offer two versions of the code. Both are written in MATLAB. 
* rbm2mps.m
Constructs the MPS with the bond dimension D equals the number of cut connections at the bipartition. See Fig.2.
    * Input:	
        * W:   n_v by n_h weight matrix W
    	* a:   bias vector of n_v for visible units
	    * b:   bias vector of n_h for hidden units
	    * bpos: the vector telling which piece the hidden units belongs to. See Fig.2 
    * Output: 
        * mps: a cell of of mps tensors

* rbm2mps2.m
Constructs the MPS with bond dimension D equals to the size of min(A_{1},B_{1}). The internal bond are just copies of the physical bonds. See Fig.4. 
    * Input:      
      * W:  n\_v by n\_h weight matrix W
      * a:  bias vector of n_v for visible units
      * b:  bias vector of n_h for hidden units
    * Output: 
      * mps: a cell of of mps tensors

The bond dimension D of rbm2mps2.m is smaller than that of rbm2mps.m.

## Auxillary tensor programs ##
* MPS\_Canonicalize.m
Canonicalize a finite MPS and give us the entanglement spectrum in each MPS bond 

* tensor\_product.m 
Calculate the contraction of two tensors and permute the index with the given order.
For example 
C(a,c,m) = sum_{c}A_{a,b,m)X_{c,b}
MATLAB code:
`C = tensor_product('acm',A,'abm',X,'cb');`

* tensor\_reshape.m
For example a 4 index tensor A can be transformed into a matrix by "permute" and "reshape" 
B( ac,bd ) =  A(a,b,c,d);
MATLAB code:
`B = tensor\_reshape( A,'abcd','ac','bd')`


## Test program ##
* Example.m
Taking the RBM structure in Fig.1(a) as an example, we construct the MPS using two different approaches (Fig.2 and Fig.4 of Sec.II). The bond dimensions are shown to be consistent with Fig.2(c) and Fig.4(c). The two MPS are identical in their canonical form, which also demostrates simplification of an RBM as discussed in Sec.V.  
