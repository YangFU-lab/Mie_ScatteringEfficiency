[README.md](https://github.com/user-attachments/files/23711381/README.md)
# Mie散射效率计算程序

基于Mie散射理论计算球形粒子在不同波长和半径下的散射效率、吸收效率等光学参数。

## 作者信息

- **姓名**: Yang FU
- **研究网站**: [https://yfu-research.com/](https://yfu-research.com/)

## 引用

如果您在研究中使用了本代码，请引用以下文献，十分感谢：

**1. Fu, Y., An, Y., Xu, Y., Dai, J. G., & Lei, D. (2022). Polymer coating with gradient‐dispersed dielectric nanoparticles for enhanced daytime radiative cooling. *EcoMat*, 4(2), e12169.**  
https://doi.org/10.1002/eom2.12169

**2. Ma, X., Fu, Y., Portniagin, A., Yang, N., Liu, D., Rogach, A. L., ... & Lei, D. (2022). Effects of Stokes shift and Purcell enhancement on fluorescence-assisted radiative cooling. *Journal of Materials Chemistry A*, 10(37), 19635-19640.**
https://doi.org/10.1039/D2TA02259A

**3. Li, J., Fu, Y., Zhou, J., Yao, K., Ma, X., Gao, S., ... & Yu, X. (2023). Ultrathin, soft, radiative cooling interfaces for advanced thermal management in skin electronics. *Science advances*, 9(14), eadg1837.**
https://doi.org/10.1126/sciadv.adg1837


## 📋 功能特性

- 计算球形粒子的Mie散射效率
- 支持自定义波长范围和粒子半径范围
- 计算散射效率、吸收效率、后向散射效率
- 计算散射截面和吸收截面
- 可视化介质和粒子的光学常数
- 支持不同材料的光学常数（折射率和消光系数）

## 🔧 依赖项

### 必需函数

- `Mie.m` - Mie散射计算核心函数
- `Mie_ab.m` - Mie系数计算函数（由Mie.m调用）

### 光学常数函数（需要根据实际材料提供）

代码中使用了以下函数来获取材料的光学常数，您需要提供相应的实现：

- `TiO2_n(lamda)` - 返回TiO₂的折射率（n）随波长的变化
- `TiO2_k(lamda)` - 返回TiO₂的消光系数（k）随波长的变化

**注意**：如果您的材料函数名称不同，请修改代码第48-49行。


## 🚀 使用方法

1. **确保依赖函数存在**
   - 将 `Mie.m` 和 `Mie_ab.m` 放在MATLAB路径中
   - 确保材料光学常数函数（如 `TiO2_n.m`, `TiO2_k.m`）可用

2. **运行程序**
   ```matlab
   ScatteringEfficiency_Calculation.m
   ```

3. **修改参数**（可选）
   - 修改波长范围（第16行）
   - 修改介质光学常数（第30-31行）
   - 修改粒子光学常数（第48-49行）
   - 修改粒子半径范围（第79行）

## 📊 输出结果

程序计算并存储以下结果矩阵（维度：波长 × 粒子半径）：

- `Qscat` - 散射效率（无量纲）
- `Qback_scat` - 后向散射效率（无量纲）
- `Qabs` - 吸收效率（无量纲）
- `Cscat` - 散射截面（单位：m²）
- `Cabs` - 吸收截面（单位：m²）

程序还会自动生成以下图形：
- 介质光学常数图（折射率n和消光系数k）
- 粒子光学常数图（折射率n和消光系数k）
- 粒子介电常数图（实部和虚部）

## 📝 代码结构

程序分为以下几个主要部分：

1. **定义计算参数** - 设置波长范围和物理常数
2. **设置介质光学常数** - 定义周围介质的光学性质
3. **设置粒子光学常数** - 定义散射粒子的光学性质
4. **定义粒子半径范围** - 设置要计算的粒子尺寸
5. **初始化结果矩阵** - 预分配内存
6. **Mie散射计算主循环** - 对每个波长和半径组合进行计算

## 🔍 示例应用

- 研究不同尺寸TiO₂粒子的散射特性
- 分析粒子尺寸对散射效率的影响
- 优化粒子尺寸以获得特定波长的最大散射
- 计算复合材料的有效光学常数

## ⚠️ 注意事项

1. **计算时间**：对于大量波长和半径组合，计算可能需要较长时间
2. **内存使用**：结果矩阵的大小取决于波长和半径的数量
3. **材料函数**：确保材料光学常数函数能正确处理输入的波长向量
4. **单位一致性**：注意所有物理量的单位（波长和半径都使用米）

## 📚 参考文献

- Bohren, C. F., & Huffman, D. R. (1983). *Absorption and Scattering of Light by Small Particles*. Wiley.
- Mätzler, C. (2002). MATLAB functions for Mie scattering and absorption. *Research Report No. 2002-08*, Institute of Applied Physics, University of Bern.

## 📄 许可证

请根据您的项目需要添加相应的许可证信息。

---

如有问题或建议，欢迎提交Issue或Pull Request。

