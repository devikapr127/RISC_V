module instr_dec;
wire [7:0]opcode;
wire [31:0] pc, instr;
wire [4:0] rs1, rs2, rd;
wire [2:0] func3;
wire [6:0] func7;


 assign rs1 =instr[19:15];
 assign rs2= instr[24:20];
 assign rd= instr[11:7];
 assign func3= instr[14:12];
 assign func7=instr[31:25];
 assign opcode=instr[6:0];
 
always@(posedge clk)begin
  if(rst)begin
   pc =0;
   instr=0;
  end
  else begin
   case({func7,func3}):begin
     0000000_000 : alu_op =ADD(alu_a, alu_b, alu_out);
     0100000_000 : alu_op =SUB(alu_a, alu_b, alu_out);
     0000000_001 : alu_op =SLL;
     0000000_010 : alu_op =SLT;
     0000000_011 : alu_op =SLTU;
     0000000_100 : alu_op =XOR;
     0000000_101 : alu_op =SRL;
     0100000_101 : alu_op =SRA;
     0000000_110 : alu_op =OR;
     0000000_111 : alu_op =AND;

   endcase
  end
end

//Implement each of the tasks
task ADD;
  output alu_out;
  input alu_a,alu_b;
  alu_out = alu_a + alu_b;
endtask

task SUB;
  output alu_out;
  input alu_a,alu_b;
  alu_out = alu_a - alu_b;
endtask

endmodule
