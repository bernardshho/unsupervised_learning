## Homework 3.

### Question 2.

#### Solution to 2a.

Let $X \sim \mathcal{N}(0, D)$ where $D$ is diagonal with $d_1, d_2, \ldots, d_p$ on the diagonal.

Properties of $D$

$$\det(D) = d_1 \cdot d_2 \cdot \ldots \cdot d_p = \prod_{i=1}^p d_i$$

$$D^{-1} = \text{diag}\left(\frac{1}{d_1}, \frac{1}{d_2}, \ldots, \frac{1}{d_p}\right)$$

PDF of $X$

$$f(x) = \frac{1}{(2\pi)^{p/2} |D|^{1/2}} \exp\left(-\frac{1}{2} x^T D^{-1} x\right)$$

$$= \frac{1}{(2\pi)^{p/2} (d_1 \cdot d_2 \cdot \ldots \cdot d_p)^{1/2}} \exp\left(-\frac{1}{2} x^T D^{-1} x\right)$$

Expand the quadratic form

$$x^T D^{-1} x = \frac{x_1^2}{d_1} + \frac{x_2^2}{d_2} + \cdots + \frac{x_p^2}{d_p}$$

Factor the PDF

$$f(x) = \frac{1}{(2\pi d_1)^{1/2}} \exp\left(-\frac{x_1^2}{2d_1}\right) \cdot \frac{1}{(2\pi d_2)^{1/2}} \exp\left(-\frac{x_2^2}{2d_2}\right) \cdot \ldots \cdot \frac{1}{(2\pi d_p)^{1/2}} \exp\left(-\frac{x_p^2}{2d_p}\right)$$

$$= \prod_{i=1}^p \frac{1}{\sqrt{2\pi d_i}} \exp\left(-\frac{x_i^2}{2d_i}\right)$$

This shows that $X_1, X_2, \ldots, X_p$ are independent, with $X_i \sim \mathcal{N}(0, d_i)$.

#### Solution to 2b.

**Given:** $Y \sim \mathcal{N}(0, D)$ where $D$ is diagonal with eigenvalues $\lambda_1, \lambda_2, \ldots, \lambda_p$.

**Goal:** Show that $QY \sim \mathcal{N}(0, \Sigma)$ where $\Sigma = QDQ^T$.


Let $X = Q^T Y$, which means $Y = QX$ (since $Q^T = Q^{-1}$ for orthonormal $Q$).

We want to find the distribution of $X$.

**1. Change of Variables**

For the transformation $x = Q^T y$ (equivalently, $y = Qx$), we use:

$$f_X(x) = \left|\det\left(\frac{dy}{dx}\right)\right| f_Y(y)$$

The Jacobian is:
$$\frac{dy}{dx} = Q$$

$$\det\left(\frac{dy}{dx}\right) = \det(Q)$$

**2. Determinant of Orthonormal Matrix**

Since $Q$ is orthonormal: $QQ^T = I$

Taking determinants:
$$\det(QQ^T) = \det(I)$$
$$\det(Q) \det(Q^T) = 1$$
$$[\det(Q)]^2 = 1$$
$$\det(Q) = \pm 1$$

Therefore: $|\det(Q)| = 1$

**3. Apply the Transformation**

$$f_X(x) = 1 \cdot f_Y(Qx)$$

$$f_X(x) = \frac{1}{(2\pi)^{p/2} (\lambda_1 \cdot \lambda_2 \cdot \ldots \cdot \lambda_p)^{1/2}} \exp\left(-\frac{1}{2}(Qx)^T D^{-1} (Qx)\right)$$

$$= \frac{1}{(2\pi)^{p/2} |D|^{1/2}} \exp\left(-\frac{1}{2}x^T Q^T D^{-1} Q x\right)$$

**4.Simplify using $\Sigma = QDQ^T$**

From the spectral decomposition:
$$\Sigma = QDQ^T$$
$$\Sigma^{-1} = QD^{-1}Q^T$$

(since $(QDQ^T)^{-1} = (Q^T)^{-1}D^{-1}Q^{-1} = QD^{-1}Q^T$)

Also:
$$\det(\Sigma) = \det(Q) \det(D) \det(Q^T) = \det(Q)^2 \det(D) = 1 \cdot \det(D) = \lambda_1 \cdot \lambda_2 \cdot \ldots \cdot \lambda_p$$

**5. Final Result**

$$f_X(x) = \frac{1}{(2\pi)^{p/2} |\Sigma|^{1/2}} \exp\left(-\frac{1}{2}x^T \Sigma^{-1} x\right)$$

This is the PDF of $\mathcal{N}(0, \Sigma)$.

**6. Conclusion**

Since $X = Q^T Y$ and $X \sim \mathcal{N}(0, \Sigma)$, we have:
$$Y = QX \sim \mathcal{N}(0, \Sigma)$$

Therefore: $\boxed{QY \sim \mathcal{N}(0, \Sigma)}$, which means $X \sim QY$ where $X \sim \mathcal{N}(0, \Sigma)$.

#### Solution to 2c. 


**Given:** $X \sim \mathcal{N}(0, \Sigma)$ and $w \in \mathbb{R}^p$.

**Goal:** Show that $w \cdot X \sim \mathcal{N}(0, w^T\Sigma w)$.

**1: Use the spectral decomposition**

Let $\Sigma = QDQ^T$ where $Q$ is orthonormal and $D = \text{diag}(\lambda_1, \lambda_2, \ldots, \lambda_p)$.

Choose $U = Q^T$ (which is orthonormal since $Q$ is).


**Choosing $U = Q^T$ to make $Y$ have independent entries**

Let $\Sigma = QDQ^T$ be the spectral decomposition and set $U = Q^T$.

Let $Y = UX = Q^T X$. The covariance matrix of $Y$ is:

$$\text{Cov}(Y) = \text{Cov}(Q^T X) = Q^T \cdot \text{Cov}(X) \cdot (Q^T)^T = Q^T \Sigma Q$$

$$= Q^T (QDQ^T) Q = (Q^T Q) D (Q^T Q) = I \cdot D \cdot I = D$$

Since $D$ is diagonal, $Y_1, Y_2, \ldots, Y_p$ are independent with $Y_i \sim \mathcal{N}(0, \lambda_i)$.


**2: Show that $w \cdot X = (Uw) \cdot (UX)$**

$$w \cdot X = w^T X$$

Since $U^T U = I$:
$$w^T X = w^T (U^T U) X = (Uw)^T (UX)$$

Therefore:
$$w \cdot X = (Uw) \cdot (UX)$$


**4: Express $w \cdot X$ as a sum of independent normals**

Let $c = Uw = Q^T w = (c_1, c_2, \ldots, c_p)^T$. Then:

$$w \cdot X = c \cdot Y = c^T Y = c_1 Y_1 + c_2 Y_2 + \cdots + c_p Y_p$$

Since the components are independent:
$$Y_i \sim \mathcal{N}(0, \lambda_i)$$

$$c_i Y_i \sim \mathcal{N}(0, c_i^2 \lambda_i)$$

$$\sum_{i=1}^p c_i Y_i \sim \mathcal{N}\left(0, \sum_{i=1}^p c_i^2 \lambda_i\right) \quad \text{(as independent)}$$


**6: Compute the variance**

$$\sum_{i=1}^p c_i^2 \lambda_i = c^T D c = (Q^T w)^T D (Q^T w)$$

$$= w^T Q D Q^T w = w^T \Sigma w$$


$$\boxed{w \cdot X \sim \mathcal{N}(0, w^T \Sigma w)}$$

This shows that any linear projection of a multivariate normal is a univariate normal.