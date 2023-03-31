![[Screenshot 2023-02-10 at 09.24.21.png]]
1. $p(x,y,z) = p(y|z)p(z|x)p(x)$
2. $p(x,y,z_1,z_2,z_3) = p(x|y,z_2)p(z_2|y,z_1,z_3)p(z_3|y)p(y)p(z_1)$
3. $p(x_1,x_2,y,z_1,z_2,z_3) = p(x_2|z_3)p(x_1|z_2,z_3,y)p(z_2)p(z_3|y)p(y|z_1)p(z_1)$
![[Screenshot 2023-02-10 at 09.28.10.png]]
- Look at root node and work down from there
- White we infer them they are latent we cannot see them 
- Encoders are for the unknown $q$

- Important because when training with only reconstruction loss, the latent space is very sparse, as a result in training time you haven't seen how to generate samples from your distribution $p(z)$
- Other way, if $\beta = \inf$ then KL term is large and then $q(z|x) \rightarrow p(z)$ as a result our encoder has no information about $x$
- Factorised gaussians are a convient choice for q distributions 

Mode collapse
- Can generate a good model but poor approximation to the actual distribution of interest 