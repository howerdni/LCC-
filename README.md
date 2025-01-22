# HVDC LCC 换流器无功消耗的计算

---

在传统晶闸管换流器（LCC）式 HVDC 系统中，换流器在运行时会从交流侧吸收相当可观的无功功率，通常约占直流传输功率的 40%～60%（典型范围）。要精确计算这一无功消耗，需要考虑整流或逆变工况下的触发 / 关断角、换相重叠角以及交流侧电气参数。下面给出常用的近似分析和计算方法。

---

## 1. 常用近似公式

在理想简化的分析中，忽略谐波和损耗等因素，可将换流器（无论整流或逆变）交流侧的有功功率 $P_\text{AC}$ 与无功功率 $Q_\text{AC}$ 视为：

$$
P_\text{AC} = 3 V I \cos \varphi \\
Q_\text{AC} = 3 V I \sin \varphi
$$

其中：

- $V$ 为交流侧相应的相电压（或线电压，需与电流取值一致）。  
- $I$ 为交流侧的基波电流幅值（或有效值，需与电压取值一致）。  
- $\varphi$ 为电流基波与电压基波之间的相位差（即功率因数角）。

对于换流器而言，$\varphi$ 与触发角 $(\alpha)$、关断角 $(\gamma)$ 以及换相重叠角 $(\mu)$ 有直接关系。一般地，对于整流器可近似认为：

$$
\varphi \approx \alpha + \frac{\mu}{2},
$$

对于逆变器则有类似的表达（会与 $\gamma$ 相关）。基于此，可得到无功功率与有功功率之比为

$$
\frac{Q_\text{AC}}{P_\text{AC}} = \tan \varphi.
$$

由于直流侧的功率在理想情况下（忽略损耗）与交流侧有功功率近似相等，令 $P_\text{DC} \approx P_\text{AC} = P$，则有

$$
Q_\text{AC} \approx P \,\tan\bigl(\alpha + \tfrac{\mu}{2}\bigr).
$$

这是常用的“功率因数角”法来快速估算换流器无功需求的经典公式。实际工程中，还需结合系统运行点（$\alpha$、$\gamma$、$\mu$ 的变化）以及换流器变压器漏抗、电网短路比等因素进行修正。

---

## 2. 换相重叠角 $\mu$ 的估算

换相重叠角 $\mu$ 主要由系统短路容量、换流变压器漏抗、直流电流等决定。若记换流变压器等效漏抗为 $X$、线路电压为 $U_\text{L}$（线电压有效值），直流电流为 $I_\text{d}$，则常用近似为：

$$
\mu \approx \frac{180^\circ}{\pi} \cdot \frac{X \cdot I_\text{d}}{U_\text{L}},
$$

其中角度用电气度（°）表示。当直流电流较大或系统阻抗较大时，$\mu$ 增加，意味着换相过程更加“钝”，从而无功消耗也随之增加。

---

## 3. 工程常用的经验值

- **无功消耗范围**：无功消耗通常约为有功功率的 40%～60%。  
- **整流侧**：  
  - 触发角 $\alpha$ 多在 15°～20°。  
  - 换相重叠角 $\mu$ 在 10°～15° 左右。  
  - 则 $\varphi \approx \alpha + \frac{\mu}{2}$ 在 20°～27° 左右；$\tan(\varphi)$ 大约 0.36～0.51，即无功消耗约在 36
