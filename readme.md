# Adder Subtractor 
### Half adder formula
```verilog
S = A xor B
C = A and B
```

### Full using half adder
![](fullusinghalf.jpg)
### Full adder direct formla
```verilog
S = A xor B xor C 
C = AB + BC + AC
```
### Main Circuit
![](addSub.png)
### Verilog code
```verilog
module adder_subtractor(s, cout, a, b, mode);
    input [3:0] a, b;
    input mode;
    output [3:0] s;
    output cout;
    wire c0, c1, c2;
    full_adder fa1(s[0], c0, a[0], (b[0]^mode), mode);
    full_adder fa2(s[1], c1, a[1], (b[1]^mode), c0);
    full_adder fa3(s[2], c2, a[2], (b[2]^mode), c1);
    full_adder fa4(s[3], cout, a[3], (b[3]^mode), c2);
endmodule

module full_adder(s, cout, a, b, cin);
    input a, b, cin;
    output s, cout;
    xor(s, a, b, c);
    or(cout, a && b, b && c, c && a); 
endmodule
```