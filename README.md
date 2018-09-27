# landGame_solidity
ethereum DApp
pragma solidity ^0.4.11;



contract landGame {
    address owner;
    mapping(address => uint) public balances;
    
    struct Plot {
        uint id;
        address owner;
        bool for_sale;
        uint price;
    }
    
    Plot[12] public plots;
    
    constructor() public {
        owner = msg.sender;
    
        for(uint i=0 ; i< plots.length;i++) {
            plots[i].id = i+1;
            plots[i].for_sale = true;
            plots[i].price = 4000;
        }
    }
    
    function getPlots() public view returns(address[], bool[], uint[]) {
        address[] memory get_addresses = new address[](12);
        bool[] memory get_status = new bool[](12);
        uint[] memory get_prices = new uint[](12);
        
        for(uint i=0 ; i< plots.length;i++) {
            Plot storage each_plot = plots[i];
            get_addresses[i] = each_plot.owner;
            get_status[i] = each_plot.for_sale;
            get_prices[i] = each_plot.price;
        }
        return(get_addresses, get_status, get_prices);
    }
}
