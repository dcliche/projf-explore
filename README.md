# Project F - FPGA Development

Project F is a little oasis where you can quench your thirst for FPGA knowledge, where you can find accessible, [open-source](LICENSE) designs to learn from and build on. Our main projects are the _Verilog Library_ and _FPGA Graphics_ tutorial series; read on to learn more.

Get an introduction with [About Project F](https://projectf.io/about/), follow [@WillFlux](https://twitter.com/WillFlux) for updates, and join the FPGA discussion on [1BitSquared Discord](https://1bitsquared.com/pages/chat). Take a peek into the future with our [roadmap](ROADMAP.md). 

![](doc/img/fpga-ad-astra.png?raw=true "")

_Image generated by the **greetings** demo from [Ad Astra](graphics/ad-astra) on a Nexys Video FPGA board._

## Verilog Library

The Project F Library includes handy Verilog designs for everyone. From framebuffers and video output to division and square root, rom and ram, and even circle drawing. You can freely build on these [MIT licensed](LICENSE) designs for commercial and non-commercial projects.

See [Library](lib/) for details or discover about the [background to the Library](https://projectf.io/posts/verilog-library-announcement/).

## FPGA Graphics

In this series, we explore graphics at the hardware level and get a feel for the power of FPGAs. We'll learn how screens work, play Pong, create starfields and sprites, paint Michelangelo's David, simulate life, draw lines and triangles, and animate characters and shapes. Along the way, you'll experience a range of designs and techniques, from memory and finite state machines to crossing clock domains and translating C algorithms into Verilog.

If you're new to the series, start by reading [Beginning FPGA Graphics](https://projectf.io/posts/fpga-graphics/).

* **Beginning FPGA Graphics**: [Designs](graphics/fpga-graphics) - [Blog](https://projectf.io/posts/fpga-graphics/)
* **Racing the Beam**: [Designs](graphics/racing-the-beam) - [Blog](https://projectf.io/posts/racing-the-beam/)
* **FPGA Pong**: [Designs](graphics/pong) - [Blog](https://projectf.io/posts/fpga-pong/)
* **Hardware Sprites**: [Designs](graphics/hardware-sprites) - [Blog](https://projectf.io/posts/hardware-sprites/)
* **Ad Astra**: [Designs](graphics/ad-astra) - [Blog](https://projectf.io/posts/fpga-ad-astra/)
* **Framebuffers**: [Designs](graphics/framebuffers) - [Blog](https://projectf.io/posts/framebuffers/)
* **Life on Screen**: [Designs](graphics/life-on-screen) - [Blog](https://projectf.io/posts/life-on-screen/)
* **Lines and Triangles**: [Designs](graphics/lines-and-triangles) - [Blog](https://projectf.io/posts/lines-and-triangles/)
* **2D Shapes**: [Designs](graphics/2d-shapes) - [Blog](https://projectf.io/posts/fpga-shapes/)
* **Animated Shapes**: [Designs](graphics/animated-shapes) - [Blog](https://projectf.io/posts/animated-shapes/)

## Hello

A three-part introduction to FPGA development with Verilog; currently available for two boards: the Arty A7 and Nexys Video.

* **Hello Arty**: [Designs](hello/hello-arty) - [Blog 1](https://projectf.io/posts/hello-arty-1/) - [Blog 2](https://projectf.io/posts/hello-arty-2/) - [Blog 3](https://projectf.io/posts/hello-arty-3/)
* **Hello Nexys**: [Designs](hello/hello-nexys) - [Blog 1](https://projectf.io/posts/hello-nexys-1/) - [Blog 2](https://projectf.io/posts/hello-nexys-2/)

## Maths and Algorithms

Maths & Algorithms is our lastest tutorial series:

* [Numbers in Verilog](https://projectf.io/posts/numbers-in-verilog/) - working with signed and unsigned integers
* [Multiplication with FPGA DSPs](https://projectf.io/posts/multiplication-fpga-dsps) - efficient multiplication with DSPs

There are [maths demos](maths/demo) in this repo to accompany the series.

_Stay tuned for more parts in spring 2022._

## Requirements

### FPGA Architecture

Our designs seek to be vendor-neutral, but some functionality requires
support for vendor primitives. We currently support two FPGA architectures:

* **XC7** - Xilinx 7 Series FPGAs, such as Spartan-7 and Artix-7
  * `BUFG`, `MMCME2_BASE`
  * HDMI support: `OBUFDS`, `OSERDES2`
* **iCE40** - Lattice iCE40 FPGAs, such as iCE40 UltraPlus
  * `SB_IO`, `SB_PLL40_PAD`, `SB_SPRAM256KA`

We also infer block ram (BRAM), see [lib/memory](lib/memory).

Porting to other architectures should be straightforward.

## SystemVerilog?

We use a few simple features of SystemVerilog to make Verilog more pleasant:

* `logic` type is safer and less work than using `wire` and `reg`
* `always_comb` and `always_ff` to make intent clear and catch mistakes
* `$clog2` to calculate vector widths (e.g. for addresses)
* `enum` to make finite state machines simpler to work with
* Matching names in module instances: `.clk_pix` instead of `.clk_pix(clk_pix)`

I believe these features are helpful, especially for beginners. All the SystemVerilog features used are compatible with recent versions of Verilator, Yosys, and Xilinx Vivado. However, if you need to use an older Verilog standard, you can adapt these designs without too much trouble.
