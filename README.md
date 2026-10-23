# Kestrel-1 Flight Software

A browser game that teaches embedded C++ design patterns. You are bringing up the firmware of a fictional CubeSat, Kestrel-1: each level gives you real-looking flight code with blanks to fill in, a simulated cross-compiler checks your answer, and the spacecraft gains hardware as you finish each category.

Every pattern is taught from primary sources: the people who named each technique, the ISO C++ standard, the original pattern catalogue, and NASA and ESA flight-software standards where they genuinely apply.

## Play

Open `index.html` in any modern browser. It is a single self-contained file with no build step. It loads fonts from Google Fonts and falls back to system fonts offline. Progress is saved in your browser's local storage.

To publish it with GitHub Pages: **Settings → Pages → Build and deployment → Deploy from a branch**, then choose `main` and `/ (root)`. The game will be served at `https://<your-user>.github.io/<repo-name>/`.

## What it covers

37 levels in seven categories, played in this order:

| Category | Levels | Patterns |
|---|---|---|
| RAII | 4 | Interrupt guard, SPI chip-select, `std::lock_guard` with a FreeRTOS mutex, unnamed-temporary fault |
| CRTP | 4 | Vtable-free UART driver, per-type instance limits, static sensor interface, wrong-base fault (with worked examples) |
| Dependency injection | 3 | Constructor injection, test doubles, compile-time (policy) injection |
| GoF Creational | 5 | Abstract Factory, Builder, Factory Method, Prototype, Singleton |
| GoF Structural | 7 | Adapter, Bridge, Composite, Decorator, Facade, Flyweight, Proxy |
| GoF Behavioral | 10 | Chain of Responsibility, Command, Interpreter, Iterator, Mediator, Memento, Observer, Strategy, Template Method, Visitor |
| GoF State | 4 | Nested switch, GoF State objects, transition table in flash, Harel hierarchy fault |

Fill-in levels check each blank and report compiler-style errors on the right line. "Fault injection" levels show broken flight code and ask you to diagnose it. You score more for fast first-try builds and long streaks; hints cost points.

## Primary sources

**RAII**
- Stroustrup, B. *The Design and Evolution of C++*. Addison-Wesley, 1994. §16.5, pp. 388–389.
- ISO/IEC 14882 (the C++ standard): [stmt.jump], [class.temporary], [thread.req.lockable.basic], [thread.lock.guard].
- Stroustrup, B. & Sutter, H. (eds.) *C++ Core Guidelines*: R.1, CP.20. https://isocpp.github.io/CppCoreGuidelines/

**CRTP**
- Coplien, J. O. "Curiously Recurring Template Patterns." *C++ Report*, February 1995, pp. 24–27.
- ISO/IEC TR 18015:2006, *Technical Report on C++ Performance*: §2.3.3, §2.5, §4.1.
- ISO/IEC 14882: [expr.static.cast].

**Dependency injection**
- Fowler, M. "Inversion of Control Containers and the Dependency Injection pattern." January 2004. https://martinfowler.com/articles/injection.html
- Alexandrescu, A. *Modern C++ Design*. Addison-Wesley, 2001. Ch. 1, Policy-Based Class Design.

**GoF patterns**
- Gamma, E., Helm, R., Johnson, R. & Vlissides, J. *Design Patterns: Elements of Reusable Object-Oriented Software*. Addison-Wesley, 1994. Each level cites the pattern's page. Pattern intents in the game are paraphrased.
- Stroustrup & Sutter, *C++ Core Guidelines*: I.3, C.35.
- Lockheed Martin, *Joint Strike Fighter Air Vehicle C++ Coding Standards*, Rev C, 2005: AV Rule 206.
- ISO/IEC 14882: [stmt.dcl], [stmt.ranged], [variant.visit].

**State machines**
- Harel, D. "Statecharts: A visual formalism for complex systems." *Science of Computer Programming* 8(3), 1987, pp. 231–274.
- Samek, M. *Practical UML Statecharts in C/C++*, 2nd ed. Newnes, 2008.

**NASA and ESA**
- Holzmann, G. J. (NASA JPL). "The Power of 10: Rules for Developing Safety-Critical Code." *IEEE Computer* 39(6), 2006, pp. 95–99.
- NASA JPL, *F´ (F Prime) flight software framework*. https://fprime.jpl.nasa.gov/
- ECSS-E-ST-70-41C, *Telemetry and telecommand packet utilization* (ESA PUS), 15 April 2016.
- ESA BSSC, *C and C++ Coding Standards*, BSSC(2000)1, Issue 1, 2000 (further reading).

Vendor APIs in the snippets (Arm CMSIS-Core, FreeRTOS, STM32 HAL) are only the hardware layer the patterns sit on. The code is written for teaching and is intentionally partial; it is not flight-qualified.
