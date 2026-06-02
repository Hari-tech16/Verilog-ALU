`timescale 1ns / 1ps

module alu(
    input [3:0] A,
    input [3:0] B,
    input [2:0] ALU_Sel,
    output reg [3:0] Result,
    output reg Carry
    );

always @(*) begin
    Carry = 0; // default carry
    case(ALU_Sel)
        3'b000: {Carry, Result} = A + B;      // ADD
        3'b001: {Carry, Result} = A - B;      // SUB
        3'b010: Result = A & B;               // AND
        3'b011: Result = A | B;               // OR
        3'b100: Result = A ^ B;               // XOR
        3'b101: Result = ~A;                  // NOT A
        3'b110: Result = A;                   // Pass A
        default: Result = 4'b0000;            // default case
    endcase
end

endmodule
