নিচের কোডটিতে prototype implement করুন:

````js
function CustomPC(cpu, ram, board) {
    this.cpu = cpu;
    this.ram = ram;
    this.board = board;
    this.buildPC = function () {
        return 'A PC with CPU ' + this.cpu + ', RAM ' + this.ram + ' and Motherboard ' + this.board + ' is built!'
    }
}

const pc1 = new CustomPC('Intel Core i9 11900', 'Corsair 16GB 3200GHz', 'ASUS G1 Sniper');
console.log(pc1.buildPC());

const pc2 = new CustomPC('Apple M1 Pro Max', 'Corsair 16GB 3200GHz', 'Foxcon M1 Board');
console.log(pc2.buildPC());
````