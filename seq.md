seq [options] <start> <end>

 seq 1 5

- Generate a Sequence with a Custom Step (Increment):
      seq 1 2 8
- Generate a Sequence of Decimal Numbers:
      seq 1 0.5 6
- Format:
     seq -f "%.2f" 1 0.5 3
- Set the separator between the numbers:
     seq -s ","  1 8
- -w: Pads the numbers with leading zeros to make them the same width:
     seq -w  1 5
