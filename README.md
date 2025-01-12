# crypto-dao-app
"use client";
import React from "react";

function MainComponent() {
  const [activeTab, setActiveTab] = useState("proposals");
  const [proposals, setProposals] = useState([
    {
      id: 1,
      title: "Treasury Allocation",
      description: "Allocate 1000 tokens for marketing",
      votes: 156,
      status: "Active",
    },
    {
      id: 2,
      title: "New Partnership",
      description: "Strategic partnership with DeFi protocol",
      votes: 89,
      status: "Active",
    },
    {
      id: 3,
      title: "Protocol Upgrade",
      description: "Implement new security features",
      votes: 234,
      status: "Closed",
    },
  ]);

  const [treasuryStats] = useState({
    totalBalance: "1,234,567 USDC",
    tokenPrice: "$2.45",
    marketCap: "$24.5M",
    holders: "3,456",
  });

  return (
    <div className="min-h-screen bg-[#0a0b0d] text-white p-4 md:p-8">
      <div className="max-w-6xl mx-auto">
        <header className="flex flex-col md:flex-row justify-between items-center mb-8">
          <h1 className="text-3xl font-bold font-roboto mb-4 md:mb-0">
            CryptoDAO
          </h1>
          <button className="bg-[#2d6cdf] hover:bg-[#2457b7] px-6 py-2 rounded-lg font-roboto">
            Connect Wallet
          </button>
        </header>

        <div className="grid grid-cols-1 md:grid-cols-4 gap-4 mb-8">
          <div className="bg-[#1a1b1e] p-4 rounded-lg">
            <p className="text-[#8b8c8e] font-roboto">Treasury Balance</p>
            <p className="text-xl font-bold font-roboto">
              {treasuryStats.totalBalance}
            </p>
          </div>
          <div className="bg-[#1a1b1e] p-4 rounded-lg">
            <p className="text-[#8b8c8e] font-roboto">Token Price</p>
            <p className="text-xl font-bold font-roboto">
              {treasuryStats.tokenPrice}
            </p>
          </div>
          <div className="bg-[#1a1b1e] p-4 rounded-lg">
            <p className="text-[#8b8c8e] font-roboto">Market Cap</p>
            <p className="text-xl font-bold font-roboto">
              {treasuryStats.marketCap}
            </p>
          </div>
          <div className="bg-[#1a1b1e] p-4 rounded-lg">
            <p className="text-[#8b8c8e] font-roboto">Token Holders</p>
            <p className="text-xl font-bold font-roboto">
              {treasuryStats.holders}
            </p>
          </div>
        </div>

        <div className="flex space-x-4 mb-6">
          <button
            onClick={() => setActiveTab("proposals")}
            className={`px-4 py-2 rounded-lg font-roboto ${
              activeTab === "proposals"
                ? "bg-[#2d6cdf] text-white"
                : "bg-[#1a1b1e] text-[#8b8c8e]"
            }`}
          >
            Proposals
          </button>
          <button
            onClick={() => setActiveTab("vote")}
            className={`px-4 py-2 rounded-lg font-roboto ${
              activeTab === "vote"
                ? "bg-[#2d6cdf] text-white"
                : "bg-[#1a1b1e] text-[#8b8c8e]"
            }`}
          >
            Vote
          </button>
        </div>

        <div className="bg-[#1a1b1e] rounded-lg p-6">
          {activeTab === "proposals" && (
            <div>
              <div className="flex justify-between items-center mb-6">
                <h2 className="text-2xl font-bold font-roboto">
                  Active Proposals
                </h2>
                <button className="bg-[#2d6cdf] hover:bg-[#2457b7] px-6 py-2 rounded-lg font-roboto">
                  Create Proposal
                </button>
              </div>
              <div className="space-y-4">
                {proposals.map((proposal) => (
                  <div
                    key={proposal.id}
                    className="bg-[#252629] p-4 rounded-lg"
                  >
                    <div className="flex justify-between items-start mb-2">
                      <h3 className="text-lg font-bold font-roboto">
                        {proposal.title}
                      </h3>
                      <span
                        className={`px-3 py-1 rounded-full text-sm ${
                          proposal.status === "Active"
                            ? "bg-[#2d6cdf] text-white"
                            : "bg-[#3a3b3e] text-[#8b8c8e]"
                        }`}
                      >
                        {proposal.status}
                      </span>
                    </div>
                    <p className="text-[#8b8c8e] mb-3 font-roboto">
                      {proposal.description}
                    </p>
                    <div className="flex items-center text-sm text-[#8b8c8e]">
                      <i className="fas fa-check-circle mr-2"></i>
                      <span>{proposal.votes} votes</span>
                    </div>
                  </div>
                ))}
              </div>
            </div>
          )}

          {activeTab === "vote" && (
            <div className="text-center py-8">
              <h2 className="text-2xl font-bold mb-4 font-roboto">
                Voting Power
              </h2>
              <p className="text-[#8b8c8e] font-roboto">
                Connect your wallet to view your voting power and participate in
                governance
              </p>
            </div>
          )}
        </div>
      </div>
    </div>
  );
}

export default MainComponent;
